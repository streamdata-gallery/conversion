---
swagger: "2.0"
x-collection-name: Click Meter
x-complete: 0
info:
  title: Click Meter Modify the association between a conversion and multiple datapoints
  description: Modify the association between a conversion and multiple datapoints.
  contact:
    name: Api Support
    url: http://www.clickmeter.com/api
    email: api@clickmeter.com
  version: v2
host: apiv2.clickmeter.com:80
basePath: /
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /aggregated/summary/conversions:
    get:
      summary: Retrieve statistics about a subset of conversions for a timeframe with
        conversions data
      description: Retrieve statistics about a subset of conversions for a timeframe
        with conversions data.
      operationId: getAggregatedSummaryConversions
      x-api-path-slug: aggregatedsummaryconversions-get
      parameters:
      - in: query
        name: fromDay
        description: If using a custom timeFrame you can specify the starting day
          (YYYYMMDD)
      - in: query
        name: limit
        description: Limit results to this number
      - in: query
        name: offset
        description: Offset where to start from
      - in: query
        name: sortBy
        description: Field to sort by
      - in: query
        name: sortDirection
        description: Direction of sort asc or desc
      - in: query
        name: status
        description: Status of conversion (deleted/active)
      - in: query
        name: textSearch
        description: Filter fields by this pattern
      - in: query
        name: timeFrame
        description: Timeframe of the request
      - in: query
        name: toDay
        description: If using a custom timeFrame you can specify the ending day (YYYYMMDD)
      responses:
        200:
          description: OK
      tags:
      - Aggregated
      - Summary
      - Conversions
  /conversions:
    get:
      summary: Retrieve a list of conversions
      description: Retrieve a list of conversions.
      operationId: getConversions
      x-api-path-slug: conversions-get
      parameters:
      - in: query
        name: createdAfter
        description: Exclude conversions created before this date (YYYYMMDD)
      - in: query
        name: createdBefore
        description: Exclude conversions created after this date (YYYYMMDD)
      - in: query
        name: limit
        description: Limit results to this number
      - in: query
        name: offset
        description: Offset where to start from
      - in: query
        name: status
        description: Status of conversion (deleted/active)
      - in: query
        name: textSearch
        description: Filter fields by this pattern
      responses:
        200:
          description: OK
      tags:
      - Conversions
    post:
      summary: Create a conversion
      description: Create a conversion.
      operationId: postConversions
      x-api-path-slug: conversions-post
      parameters:
      - in: body
        name: value
        description: The body of the conversion
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Conversions
  /conversions/aggregated/list:
    get:
      summary: Retrieve statistics about this customer for a timeframe related to
        a subset of conversions grouped by some temporal entity (day/week/month)
      description: Retrieve statistics about this customer for a timeframe related
        to a subset of conversions grouped by some temporal entity (day/week/month).
      operationId: getConversionsAggregatedList
      x-api-path-slug: conversionsaggregatedlist-get
      parameters:
      - in: query
        name: fromDay
        description: If using a custom timeFrame you can specify the starting day
          (YYYYMMDD)
      - in: query
        name: groupBy
        description: The temporal entity you want to group by (week/month)
      - in: query
        name: status
        description: Status of conversion (deleted/active)
      - in: query
        name: timeFrame
        description: Timeframe of the request
      - in: query
        name: toDay
        description: If using a custom timeFrame you can specify the ending day (YYYYMMDD)
      responses:
        200:
          description: OK
      tags:
      - Conversions
      - Aggregated
      - List
  /conversions/count:
    get:
      summary: Retrieve a count of conversions
      description: Retrieve a count of conversions.
      operationId: getConversionsCount
      x-api-path-slug: conversionscount-get
      parameters:
      - in: query
        name: createdAfter
        description: Exclude conversions created before this date (YYYYMMDD)
      - in: query
        name: createdBefore
        description: Exclude conversions created after this date (YYYYMMDD)
      - in: query
        name: status
        description: Status of conversion (deleted/active)
      - in: query
        name: textSearch
        description: Filter fields by this pattern
      responses:
        200:
          description: OK
      tags:
      - Conversions
      - Count
  /conversions/{conversionId}:
    delete:
      summary: Delete conversion specified by id
      description: Delete conversion specified by id.
      operationId: deleteConversionsConversion
      x-api-path-slug: conversionsconversionid-delete
      parameters:
      - in: path
        name: conversionId
        description: Id of the conversion
      responses:
        200:
          description: OK
      tags:
      - Conversions
      - ConversionId
    get:
      summary: Retrieve conversion specified by id
      description: Retrieve conversion specified by id.
      operationId: getConversionsConversion
      x-api-path-slug: conversionsconversionid-get
      parameters:
      - in: path
        name: conversionId
        description: Id of the conversion
      responses:
        200:
          description: OK
      tags:
      - Conversions
      - ConversionId
    post:
      summary: Update conversion specified by id
      description: Update conversion specified by id.
      operationId: postConversionsConversion
      x-api-path-slug: conversionsconversionid-post
      parameters:
      - in: path
        name: conversionId
        description: Id of the conversion
      - in: body
        name: value
        description: Updated body of the conversion
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Conversions
      - ConversionId
  /conversions/{conversionId}/aggregated:
    get:
      summary: Retrieve statistics about this conversion for a timeframe
      description: Retrieve statistics about this conversion for a timeframe.
      operationId: getConversionsConversionAggregated
      x-api-path-slug: conversionsconversionidaggregated-get
      parameters:
      - in: path
        name: conversionId
        description: Id of the conversion
      - in: query
        name: favourite
        description: Is the datapoint marked as favourite
      - in: query
        name: fromDay
        description: If using a custom timeFrame you can specify the starting day
          (YYYYMMDD)
      - in: query
        name: hourly
        description: If using yesterday or today timeframe you can ask for the hourly
          detail
      - in: query
        name: tag
        description: Filter by this tag name
      - in: query
        name: timeFrame
        description: Timeframe of the request
      - in: query
        name: toDay
        description: If using a custom timeFrame you can specify the ending day (YYYYMMDD)
      responses:
        200:
          description: OK
      tags:
      - Conversions
      - ConversionId
      - Aggregated
  /conversions/{conversionId}/aggregated/list:
    get:
      summary: Retrieve statistics about this conversion for a timeframe grouped by
        some temporal entity (day/week/month)
      description: Retrieve statistics about this conversion for a timeframe grouped
        by some temporal entity (day/week/month).
      operationId: getConversionsConversionAggregatedList
      x-api-path-slug: conversionsconversionidaggregatedlist-get
      parameters:
      - in: path
        name: conversionId
        description: Id of the conversion
      - in: query
        name: fromDay
        description: If using a custom timeFrame you can specify the starting day
          (YYYYMMDD)
      - in: query
        name: groupBy
        description: The temporal entity you want to group by (week/month)
      - in: query
        name: timeFrame
        description: Timeframe of the request
      - in: query
        name: toDay
        description: If using a custom timeFrame you can specify the ending day (YYYYMMDD)
      responses:
        200:
          description: OK
      tags:
      - Conversions
      - ConversionId
      - Aggregated
      - List
  /conversions/{conversionId}/datapoints:
    get:
      summary: Retrieve a list of datapoints connected to this conversion
      description: Retrieve a list of datapoints connected to this conversion.
      operationId: getConversionsConversionDatapoints
      x-api-path-slug: conversionsconversioniddatapoints-get
      parameters:
      - in: path
        name: conversionId
        description: Id of the conversion
      - in: query
        name: createdAfter
        description: Exclude datapoints created before this date (YYYYMMDD)
      - in: query
        name: createdBefore
        description: Exclude datapoints created after this date (YYYYMMDD)
      - in: query
        name: limit
        description: Limit results to this number
      - in: query
        name: offset
        description: Offset where to start from
      - in: query
        name: status
        description: Status of datapoint (deleted/active/paused/spam)
      - in: query
        name: tags
        description: Filter by this tag name
      - in: query
        name: textSearch
        description: Filter fields by this pattern
      - in: query
        name: type
        description: Type of datapoint (tl/tp)
      responses:
        200:
          description: OK
      tags:
      - Conversions
      - ConversionId
      - Datapoints
  /conversions/{conversionId}/datapoints/batch/patch:
    put:
      summary: Modify the association between a conversion and multiple datapoints
      description: Modify the association between a conversion and multiple datapoints.
      operationId: putConversionsConversionDatapointsBatchPatch
      x-api-path-slug: conversionsconversioniddatapointsbatchpatch-put
      parameters:
      - in: path
        name: conversionId
        description: Id of the conversion
      - in: body
        name: data
        description: Patch requests
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Conversions
      - ConversionId
      - Datapoints
      - Batch
      - Patch
  /conversions/{conversionId}/datapoints/count:
    get:
      summary: Retrieve a count of datapoints connected to this conversion
      description: Retrieve a count of datapoints connected to this conversion.
      operationId: getConversionsConversionDatapointsCount
      x-api-path-slug: conversionsconversioniddatapointscount-get
      parameters:
      - in: path
        name: conversionId
        description: Id of the conversion
      - in: query
        name: createdAfter
        description: Exclude datapoints created before this date (YYYYMMDD)
      - in: query
        name: createdBefore
        description: Exclude datapoints created after this date (YYYYMMDD)
      - in: query
        name: status
        description: Status of datapoint (deleted/active/paused/spam)
      - in: query
        name: tags
        description: Filter by this tag name
      - in: query
        name: textSearch
        description: Filter fields by this pattern
      - in: query
        name: type
        description: Type of datapoint (tl/tp)
      responses:
        200:
          description: OK
      tags:
      - Conversions
      - ConversionId
      - Datapoints
      - Count
  /conversions/{conversionId}/datapoints/patch:
    put:
      summary: Modify the association between a conversion and a datapoint
      description: Modify the association between a conversion and a datapoint.
      operationId: putConversionsConversionDatapointsPatch
      x-api-path-slug: conversionsconversioniddatapointspatch-put
      parameters:
      - in: path
        name: conversionId
        description: Id of the conversion
      - in: body
        name: data
        description: Patch request
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Conversions
      - ConversionId
      - Datapoints
      - Patch
  /conversions/{conversionId}/hits:
    get:
      summary: Retrieve the list of events related to this conversion.
      description: Retrieve the list of events related to this conversion..
      operationId: getConversionsConversionHits
      x-api-path-slug: conversionsconversionidhits-get
      parameters:
      - in: path
        name: conversionId
        description: Id of the conversion
      - in: query
        name: filter
        description: Filter event type (spiders/uniques/nonuniques/conversions)
      - in: query
        name: fromDay
        description: If using a custom timeFrame you can specify the starting day
          (YYYYMMDD)
      - in: query
        name: limit
        description: Limit results to this number
      - in: query
        name: offset
        description: Offset where to start from (its the lastKey field in the response
          object)
      - in: query
        name: timeframe
        description: Timeframe of the request
      - in: query
        name: toDay
        description: If using a custom timeFrame you can specify the ending day (YYYYMMDD)
      responses:
        200:
          description: OK
      tags:
      - Conversions
      - ConversionId
      - Hits
  /conversions/{conversionId}/notes:
    put:
      summary: Fast patch the "notes" field of a conversion
      description: Fast patch the "notes" field of a conversion.
      operationId: putConversionsConversionNotes
      x-api-path-slug: conversionsconversionidnotes-put
      parameters:
      - in: path
        name: conversionId
        description: Id of the conversion
      - in: body
        name: note
        description: Patch requests
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Conversions
      - ConversionId
      - Notes
  /conversions/{conversionId}/reports:
    get:
      summary: Retrieve a top report connected to this conversion
      description: Retrieve a top report connected to this conversion.
      operationId: getConversionsConversionReports
      x-api-path-slug: conversionsconversionidreports-get
      parameters:
      - in: path
        name: conversionId
        description: Id of the conversion
      - in: query
        name: fromDay
        description: If using a custom timeFrame you can specify the starting day
          (YYYYMMDD)
      - in: query
        name: hittype
        description: Type of the event you want to filter this report with
      - in: query
        name: timeframe
        description: Timeframe of the request
      - in: query
        name: toDay
        description: If using a custom timeFrame you can specify the ending day (YYYYMMDD)
      - in: query
        name: type
        description: Type of the report
      responses:
        200:
          description: OK
      tags:
      - Conversions
      - ConversionId
      - Reports
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---