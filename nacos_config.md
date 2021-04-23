```
curl -X POST "http://192.168.3.119:8848/nacos/v1/cs/configs?dataId=lumall-coupon.properties&group=DEFAULT_GROUP&content=coupon.user.name=haha%0Acoupon.user.password=004"
```

```
curl -X GET "http://192.168.3.119:8848/nacos/v1/cs/configs?dataId=lumall-coupon.properties&group=DEFAULT_GROUP"
```

