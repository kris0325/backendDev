### //Java8 stream 常用API

```java
    List<Integer> nums = Lists.newArrayList(1, 1, null, 2, 3, 4, null, 5, 6, 7, 8, 9, 10);
```



​        

```java
        System.out.println("sum is:" + nums.stream()
                .filter(num -> num != null)
                .distinct()
                .mapToInt(num -> num * 2)
                .peek(System.out::println)
                .skip(2)
                .limit(3)
                .sum());
```





#### //求最大值 最小值 　　

​     

```java
   Map<Long, List<PurchaseOrderSku>> skuPoSkuMap = purchaseOrderSkus.stream().collect(Collectors.groupingBy(PurchaseOrderSku::getSkuId));


for (Map.Entry<Long, List<PurchaseOrderSku>> entry : skuPoSkuMap.entrySet()) {
        SkuPurchasePriceDto skuPurchasePriceDto = new SkuPurchasePriceDto();
```
//求最大值 最小值

```java
 Integer maxPurchasePrice = entry.getValue().stream().mapToInt(posku -> posku.getSkuPrice()).max().getAsInt();
            Integer minPurchasePrice = entry.getValue().stream().mapToInt(posku -> posku.getSkuPrice()).min().getAsInt();
            skuPurchasePriceDto.setMaxPurchasePrice(maxPurchasePrice);
            skuPurchasePriceDto.setMinPurchasePrice(minPurchasePrice);
            skuPurchasePriceDto.setSkuId(entry.getKey());
            skuPurchasePriceDtos.add(skuPurchasePriceDto);
        }
```



​           


// lsit	去重

            List<Integer> list1 = Lists.newArrayList(1,1,2,3,4,4,5,6,6);
    
            HashSet<Integer> set = new HashSet<>(list1);
            List<Integer> distinctListBySet = new ArrayList( new HashSet<>(list1)); 
              List<Integer> distinctList = list1.stream().distinct().collect(Collectors.toList());

