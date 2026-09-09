# Spark Structured Streaming Master Notes

## Curriculum
Real-time processing patterns, Spark engine, Azure Event Hubs integration, windowing, watermarking, state management, streaming best practices.

## Mental model
```text
Event source → readStream → DataFrame transformations → state/window → writeStream → sink
```

## Batch vs streaming
Batch processes bounded data. Streaming processes continuously arriving data with incremental execution.

## Sources
Curriculum emphasizes Azure Event Hubs. Spark Structured Streaming also supports connectors such as Kafka and files depending on environment.

## Windows
Time-based windows group events into intervals. Know tumbling vs sliding concepts at a high level.

## Event time vs processing time
Event time = when the event happened.
Processing time = when the engine processes it.
Late data makes event-time handling important.

## Watermarking
A watermark tracks how far event time has advanced and allows state for sufficiently old windows to be cleaned up according to the query's semantics. It is used to bound state and handle late data.

## State management
Stateful aggregations and joins can retain information across micro-batches. State must be controlled because unbounded state consumes resources.

## Checkpointing / recovery
Structured Streaming uses checkpointing for fault tolerance and progress/state recovery. Exact guarantees depend on source/sink semantics and query design.

## Failure scenario
If a stream fails, do not say "it always starts from zero". Explain that checkpointed progress/state can allow recovery, subject to supported source/sink semantics.

## Interview questions
- Batch vs streaming?
- Event time vs processing time?
- Why watermark?
- What is stateful processing?
- How does checkpointing help?
- How do you handle late events?
- How would you recover a failed stream?
