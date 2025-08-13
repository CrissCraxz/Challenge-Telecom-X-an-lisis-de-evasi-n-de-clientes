
# 📌 Informe Final — Challenge Telecom X

## 1️⃣ Introducción
Se analizaron **7267 clientes**, con **1869** casos de churn (**25.72%**).

**Objetivos**:
- Asegurar calidad de datos (limpieza, estandarización).
- Crear variables derivadas y preparar el dataset.
- Entender distribución de churn y factores asociados.
- Generar insights y recomendaciones.

---

## 2️⃣ Limpieza y Tratamiento
- Normalización de texto (minúsculas, espacios).
- Estandarización de nombres clave: `cargo_total`, `cargo_mensual`, `meses_tenencia`, `churn`, `contrato`, `metodo_pago`, `genero`.
- Conversión numérica robusta de cargos.
- Conversión de **sí/no** a binario (1/0) en servicios y churn.
- Reglas de coherencia:
  - Sin internet ⇒ complementos de internet = 0.
  - Sin teléfono ⇒ líneas múltiples = 0.
- Nuevas columnas:
  - `cuentas_diarias` = `cargo_mensual` / 30
  - `servicios_contratados` (conteo de servicios activos)
  - `gasto_estimado` = `cargo_mensual` × `meses_tenencia`

**Incoherencias detectadas**:
- tenencia negativa: 0 registros
- cargo mensual negativo: 0 registros
- cargo total negativo: 0 registros
- tenencia0 totalpos: 0 registros
- cargos desproporcionados 20pct: 64 registros
- lineas sin telefono: 0 registros
- addons sin internet: 0 registros

---

## 3️⃣ Análisis Exploratorio de Datos
- **Churn global**: **25.72%** (1869 / 7267)


### Churn por tipo de contrato
- month-to-month: 41.32%
- one year: 10.93%
- two year: 2.75%


### Churn por método de pago
- electronic check: 43.8%
- mailed check: 18.5%
- bank transfer (automatic): 16.24%
- credit card (automatic): 14.8%


### Churn por género
- female: 26.14%
- male: 25.31%


---

## 4️⃣ Correlaciones con Churn (Top 5)
- internet_activo: 0.224
- cuentas_diarias: 0.19
- cargo_mensual: 0.19
- internet_tv: 0.062
- internet_peliculas: 0.061

---

## 5️⃣ Conclusiones e Insights
- El churn global es **25.72%**.
- El contrato con mayor churn: **month-to-month** con 41.32%.
- El método de pago con mayor churn: **electronic check** con 43.8%.
- Mayor churn en clientes con **menor tenencia**.
- La **cantidad de servicios** suele correlacionarse **negativamente** con churn (más servicios, menos churn), cuando aplica.

---

## 6️⃣ Recomendaciones
1. Migrar clientes **month-to-month** hacia **contratos de 1–2 años** con incentivos.
2. **Onboarding y soporte** intensivo en los **primeros meses** (segmento de alto riesgo).
3. Promover **paquetes** (más servicios) para aumentar retención.
4. Incentivar **métodos de pago automáticos** para reducir fricción y churn.
5. Monitoreo proactivo según **perfil de riesgo** (tenencia baja, método de pago, tipo de contrato).

