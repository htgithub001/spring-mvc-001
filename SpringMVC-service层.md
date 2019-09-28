# 关于线程安全

```
@Controller
@RequestMapping(value = "redisAllInOne")
public class RedisAllInOneController {
 
    @Autowired
    private RedisService redisService;
 
    @RequestMapping(value = "get",method = RequestMethod.GET)
    @ResponseBody
    public Object getByMyService(String key){
        try {
            String result = redisService.get(key);
            return result;
        }catch (Exception e){
            e.printStackTrace();
        }
        return null;
    }
}　　
```

上述代码中的RedisService redisService就应该是线程安全的。总之service尽量做成线程安全的，比方说底层用线程池来支持。
一旦线程的资源用尽，本程序就会开始进入等待状态，直到有线程（握有jedis客户端的线程）被释放。
