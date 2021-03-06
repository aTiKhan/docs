﻿#Data subscription events

The `Subscription` instance exposes a few events which allow to provide control over the data stream. There are four subscription events that you can hook up:

{CODE events@ClientApi\DataSubscriptions\DataSubscriptions.cs /}

Each of them is invoked on a different level of documents processing:

- `BeforeBatch` - called when a first document from the batch is about to be processed by handlers, if the batch is empty then the event is not raised,
- `BeforeAcknowledgment` - triggered after processing all documents in batch, the returned value determines if the batch can be acknowledged (default: `true`),
- `AfterAcknowledgment` - invoked after the batch processed acknowledgment had been sent to the server,
- `AfterBatch` - called after processing all docs from the batch.

