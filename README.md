# Electricity-Sector-Data-Streaming-and-Analysis
## Data Acquisition
* Automatically retrieves facility metadata (facility code, name, region, unit code, latitude, and longitude) along with 5-minute interval time-series measurements (power generation, CO2 emissions, market price, and demand) from the OpenElectricity platform.
## Data Processing & Aggregation
* Cleans and merges raw metadata with time-series records using the unit_code.
* Aggregates unit-level records into centralized facility-level records to ensure that each plant maps to exactly one structured row per timestamp.
## MQTT Data Publisher
* Transforms the aggregated records row-by-row into JSON payloads and continuously publishes them to the broker.hivemq.com public MQTT broker to simulate a live, unbounded data stream.
## MQTT Live Subscriber
* Subscribes to the designated group topic, decodes incoming JSON text payloads, and securely updates an in-memory live dataset utilizing thread locks (threading.Lock) for safe concurrent read/writes.
## Interactive Dashboard Visualization
* Powered by Dash and Dash Leaflet. It renders polygon state boundaries (NEM network regions like NSW1, QLD1, VIC1, SA1, TAS1) using GeoJSON files and plots facility markers dynamically. It supports multi-dimensional filtering and detailed click-event popups.
