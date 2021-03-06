---
-api-id: P:Windows.Devices.Sensors.Barometer.ReportInterval
-api-type: winrt property
---

<!-- Property syntax
public uint ReportInterval { get;  set; }
-->

# Windows.Devices.Sensors.Barometer.ReportInterval

## -description
Gets or sets the current report interval for the barometer.

## -property-value
The current report interval.

## -remarks
The report interval is specified in milliseconds.

The report interval will be set to a default value that will vary based on the sensor driver’s implementation. If your app does not want to use this default value, you should set the report interval to a non-zero value prior to registering an event handler or calling [GetCurrentReading](barometer_getcurrentreading_1416488181.md). The sensor will then attempt to allocate resources to satisfy the application’s requirements but the sensor also has to balance the needs of other apps using the sensor.

Changes to the report interval after an event handler has been registered or [GetCurrentReading](barometer_getcurrentreading_1416488181.md) has been called may apply to the delivery of subsequent sensor readings.

Conversely, when an application is finished with the sensor, it should explicitly return the sensor to its default report interval by setting it to zero. This is important for power conservation, especially when using a language that may keep the sensor object active for an indefinite period prior to garbage collection.

Your application should consult the [MinimumReportInterval](barometer_minimumreportinterval.md) property prior to setting the report interval to ensure that the sensor can honor the requested report interval. Setting a value below the minimum supported interval will either trigger an exception or have undefined results.

Setting a value of zero requests the driver to use its default report interval. As with requesting a specific interval, the driver may choose a different interval based on other client requests and internal logic.

## -examples

## -see-also
