# PostAir Weather API - Baseline Performance & Functional Tests

An automated API test suite created from an OpenAPI 3.1 contract to validate response timing, server latency metrics, and payload size bounds against mock and live endpoints.

---

## 📁 Repository Contents

- `PostAir Weather API.postman_collection.json` - Complete Postman collection with functional and performance assertions.
- `Dev Env.postman_environment.json` - Environment variables configuring mock server URLs (`baseUrl`) and API keys.
- `instructor_5u8wl14w3sk0sv0ia7uf70501_public_1773788129_postair-weather-api.yaml` - OpenAPI 3.1 specification for the weather services.

---

## ⚡ Non-Functional Performance Assertions

Each endpoint runs the following automated validation scripts:

1. **Database Query Performance (`Server-Timing` header)**
   - Validates that server-side database duration remains under 100ms.
2. **Audit Logging & Warning Flags**
   - Logs request response times and triggers console warnings when latency exceeds 1000ms.
3. **Latency SLA Threshold**
   - Asserts response times remain well within the acceptable SLA ceiling (`< 20000ms`).
4. **Payload Size Guardrail**
   - Enforces response body payloads remain below 10 KB to avoid network saturation.

---

## 🚀 How to Run

1. Import `PostAir Weather API.postman_collection.json` into Postman.
2. Import `Dev Env.postman_environment.json` and set it as the active environment.
3. Run the collection via Postman Collection Runner or Newman CLI:
   ```bash
   newman run "PostAir Weather API.postman_collection.json" -e "Dev Env.postman_environment.json"