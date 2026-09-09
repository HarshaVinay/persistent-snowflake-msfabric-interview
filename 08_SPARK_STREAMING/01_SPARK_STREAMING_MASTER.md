# Spark Structured Streaming Master Notes

## Batch vs streaming
Batch processes bounded data. Streaming processes continuously arriving data, often with event-time semantics.

## Core flow
`source → readStream → DataFrame transformations → window/stateful logic → writeStream → sink`.

## Event time vs processing time
Event time is when the business event occurred. Processing time is when Spark processes it. Event time is important when records can arrive late or out of order.

## Windows
Tumbling windows are fixed non-overlapping intervals. Sliding windows overlap and use a duration + slide interval. Session windows group activity separated by inactivity gaps.

## Watermarking
A watermark tells the engine how much late data it is prepared to handle for stateful event-time operations. It helps bound state growth; it does not magically make arbitrarily late data correct.

## State management
Stateful aggregations/join patterns maintain intermediate information across micro-batches. State should be bounded with appropriate keys, windows and watermarks where applicable.

## Checkpointing
Checkpoints persist streaming query progress/state so a query can recover after failure. Checkpoint location must be stable and appropriate for the query.

## Output modes
Know append, update and complete at a conceptual level and match the mode to the operation/sink semantics.

## Sources
Your curriculum explicitly includes Azure Event Hubs. Also understand the general concept of Kafka/files and streaming sources without assuming a specific vendor.

## Interview scenario
“Events arrive 10 minutes late.”
Answer: use event-time processing and an appropriate watermark/window policy, explain the accepted lateness and what happens to records beyond the watermark. Validate sink semantics and recovery using checkpoints.
