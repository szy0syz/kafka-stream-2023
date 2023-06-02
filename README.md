# kafka-stream-2023

## Menu

1. Getting Started
2. Basic Operations
3. Hands On: Basic Operations
4. KTable
5. Hands On: KTable
6. Serialization
7. Joins
8. Hands On: Joins
9. Stateful Operations
10. Hands On: Aggregations
11. Windowing
12. Hands On: Windowing
13. Time Concepts
14. Hands On: Time Concepts
15. Processor API
16. Hands On: Processor API
17. Testing
18. Hands On: Testing
19. Error Handling
20. Hands On: Error Handling
21. Internals
22. Stateful Fault Tolerance
23. Interactive Queries

![image](https://github.com/szy0syz/kafka-stream-2023/assets/10555820/376f914a-f729-4434-b65f-305a4a13a5d2)

## 没有对比就没有伤害

```java
public static void main(String[] args) {
 try(Consumer<String, Widget> consumer = new KafkaConsumer<>(consumerProperties());
    Producer<String, Widget> producer = new KafkaProducer<>(producerProperties())) {
        consumer.subscribe(Collections.singletonList("widgets"));
        while (true) {
            ConsumerRecords<String, Widget> records =    consumer.poll(Duration.ofSeconds(5));
                for (ConsumerRecord<String, Widget> record : records) {
                    Widget widget = record.value();
                    if (widget.getColour().equals("red") {
                        ProducerRecord<String, Widget> producerRecord = new ProducerRecord<>("widgets-red", record.key(), widget);
                        producer.send(producerRecord, (metadata, exception)-> {…….} );
```

```java
final StreamsBuilder builder = new StreamsBuilder();
builder.stream(“widgets”, Consumed.with(stringSerde, widgetsSerde))
    .filter((key, widget) -> widget.getColour.equals("red"))
    .to("widgets-red", Produced.with(stringSerde, widgetsSerde));
```

- 终于用Con.io的免费云跑起来了

<img width="460" alt="image" src="https://github.com/szy0syz/kafka-stream-2023/assets/10555820/18eb319d-185f-424a-a886-d9bbb290bb65">
