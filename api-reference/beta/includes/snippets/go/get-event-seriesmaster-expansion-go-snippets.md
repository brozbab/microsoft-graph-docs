---
description: "Automatically generated file. DO NOT MODIFY"
---

```go

//THE GO SDK IS IN PREVIEW. NON-PRODUCTION USE ONLY
graphClient := msgraphsdk.NewGraphServiceClient(requestAdapter)

requestParameters := &graphconfig.MeEventItemRequestBuilderGetQueryParameters{
	Select: [] string {"subject","start","end","occurrenceId","exceptionOccurrences","cancelledOccurrences"},
	Expand: [] string {"exceptionOccurrences"},
}
configuration := &graphconfig.MeEventItemRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

result, err := graphClient.Me().EventsById("event-id").Get(context.Background(), configuration)


```