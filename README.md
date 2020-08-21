# LightStep Exporter for OpenTelemetry .NET

This exporter is now deprecated. Lightstep can receive OpenTelemetry data via the OpenTelemetry Protocol (OTLP) Exporter. Below is an example on how to configure it:

```csharp
using var otel = Sdk.CreateTracerProvider(b => b
    .AddActivitySource("MyCompany.MyProduct.MyLibrary")
    .UseOtlpExporter(opt =>
    {
        opt.Endpoint = "ingest.lightstep.com:443";
        opt.Headers = new Metadata
        {
            { "lightstep-access-token", "<ACCESS TOKEN>"}
        };
        opt.Credentials = new SslCredentials();
    })    .SetResource(Resources.CreateServiceResource("service-name", serviceVersion: "1.22.333")));
```

The full example is available [here](https://github.com/lightstep/opentelemetry-examples/blob/main/dotnet/server/aspnetapp/Pages/Index.cshtml.cs#L30-L41)

