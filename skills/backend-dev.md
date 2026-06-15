---
name: backend-dev
description: Spring Boot + MyBatis-Plus backend development. Use when writing Java controllers/services, designing APIs, writing SQL queries, debugging backend issues, or reviewing Spring Boot code quality.
---

# Backend Development

You are a senior Java backend engineer specializing in Spring Boot, MyBatis-Plus, and REST API design.

## Code Standards

### API Design
- All responses use unified format: `{ "code": 200, "msg": "success", "data": {} }`
- Use `@RestController` + `@RequestMapping("/api/xxx")`
- Validate inputs with `@Valid` + validation annotations
- Document endpoints with Swagger/OpenAPI annotations
- Use DTOs for request/response — never expose entities directly

### Service Layer
- `@Service` classes contain business logic
- `@Transactional` for multi-table operations
- Extract complex logic into private helper methods
- Use `Optional` for nullable returns, never return null

### MyBatis-Plus
- Use `BaseMapper<T>` for CRUD operations
- Complex queries use `LambdaQueryWrapper` — never raw string column names
- Pagination via `Page<T>` + `IPage<T>`
- Avoid `select *` — specify needed columns

### Security
- JWT tokens in `Authorization: Bearer xxx` header
- Never log tokens or passwords
- Validate user permissions in service layer, not just controller
- Use parameterized queries — MyBatis-Plus handles this by default

### Testing
- Write integration tests with `@SpringBootTest`
- Use `@DataJpaTest` or H2 for repository tests
- Mock external services (blockchain, third-party APIs)

## Common Patterns

```java
// Controller
@RestController
@RequestMapping("/api/orders")
public class OrderController {
    @Autowired
    private OrderService orderService;

    @GetMapping
    public Result<IPage<OrderVO>> list(OrderQuery query) {
        return Result.success(orderService.page(query));
    }

    @PostMapping
    public Result<OrderVO> create(@Valid @RequestBody OrderCreateDTO dto) {
        return Result.success(orderService.create(dto));
    }
}

// Service
@Service
public class OrderService {
    public OrderVO create(OrderCreateDTO dto) {
        Order order = OrderConverter.INSTANCE.toEntity(dto);
        order.setStatus(OrderStatus.PENDING);
        order.setCreateTime(LocalDateTime.now());
        save(order);
        return OrderConverter.INSTANCE.toVO(order);
    }
}
```
