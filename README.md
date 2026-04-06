Aquí tienes el **README.md completo y profesional** listo para copiar y pegar directamente en tu repositorio:

```markdown
# 🛡️ Analizador Unificado de Seguridad – Correos, Contratos y Boletines

![Python](https://img.shields.io/badge/python-3.11-blue)
![FastAPI](https://img.shields.io/badge/FastAPI-0.101.1-lightgrey)
![License](https://img.shields.io/badge/license-MIT-green)

Este repositorio contiene una **herramienta profesional en Python** para analizar automáticamente:

- **Correos sospechosos (.msg)**
- **Contratos (Word + Excel)**
- **Boletines de seguridad (PDF)**

Genera **reportes profesionales** con IA, evidencias, scoring de riesgo y explicaciones humanizadas.

---

## 📁 Estructura del proyecto

```text
analizador_unificado/
├── api/
│   └── main.py                  ← Endpoint HTTP (FastAPI)
├── core/
│   ├── orchestrator.py          ← Flujo principal unificado
│   └── utils.py                 ← Funciones auxiliares
├── modules/
│   ├── correos/
│   │   ├── parser_email.py      ← Extrae contenido del correo
│   │   ├── analyzer.py          ← Analiza links, adjuntos y sospecha
│   │   └── scorer.py            ← Scoring de riesgo de correo
│   ├── contratos/
│   │   ├── parser_word.py       ← Parseo de contratos Word
│   │   ├── parser_excel.py      ← Parseo de Excel de respuestas
│   │   ├── comparator.py        ← Comparación Word ↔ Excel
│   │   └── scorer.py            ← Scoring de cumplimiento
│   └── boletines/
│       ├── parser_pdf.py               ← Parseo de PDF
│       ├── vulnerability_extractor.py ← Extrae CVE, producto, versión
│       ├── inventory_checker.py        ← Compara con inventario de la empresa
│       └── scorer.py                   ← Scoring de impacto
├── ai/
│   └── explanation_generator.py ← Genera explicaciones y correcciones con IA
├── reporting/
│   ├── report_generator.py      ← Genera Word final con evidencias
│   └── templates/
│       ├── plantilla_contrato.docx
│       └── plantilla_boletin.docx
├── storage/
│   ├── temp/
│   ├── evidencias/
│   └── reportes/
├── config/
│   └── settings.example.py      ← Ejemplo de configuración
├── docs/                        ← Diagramas y documentación visual
├── examples/                    ← Archivos de prueba (.msg, .docx, .xlsx, .pdf)
├── requirements.txt
└── README.md
```

---

## ⚡ Flujo de funcionamiento unificado

```text
Power Automate / Cliente HTTP
   ↓ (POST JSON + archivos: .msg, .docx, .xlsx, .pdf)
API Python (FastAPI)
   ↓
Orquestador principal (orchestrator.py)
   ↓
[1] Parser Email (correos)
[2] Parser Word + Parser Excel (contratos)
[3] Parser PDF + Extractor CVE (boletines)
[4] Comparador y Validador (contratos y boletines)
[5] Scoring y riesgo (correos, contratos, boletines)
[6] Generador de explicaciones IA (OpenAI GPT-4.1-mini)
[7] Generador de reporte Word final con evidencias
   ↓
Respuesta JSON + reporte en Base64
```

---

## 🔧 Instalación

```bash
git clone https://github.com/AngelGabriel777/mailware.git
cd mailware
python -m venv venv
# Activar entorno virtual
source venv/bin/activate   # Linux / Mac
venv\Scripts\activate      # Windows
# Instalar dependencias
pip install -r requirements.txt
```

---

## 🧰 Librerías y herramientas principales

| Función                   | Librerías / Herramientas      | Gratuitas?           |
| ------------------------- | ----------------------------- | -------------------- |
| API / Servidor            | `fastapi`, `uvicorn`          | ✅                    |
| Parsear Word              | `python-docx`                 | ✅                    |
| Leer Excel                | `pandas`, `openpyxl`          | ✅                    |
| Parsear PDF               | `pdfplumber`, `PyPDF2`        | ✅                    |
| Parsear Correos           | `extract-msg`, `tldextract`   | ✅                    |
| Regex / Comparación texto | `re`, `fuzzywuzzy` (opcional) | ✅                    |
| Generar texto con IA      | `openai`                      | ❌ (pago por consumo) |
| Generar Word final        | `python-docx`                 | ✅                    |
| Base64                    | `base64` (builtin)            | ✅                    |

---

## ⚙️ Configuración

Crea `config/settings.py` basado en `settings.example.py`:

```python
OPENAI_API_KEY = "TU_API_KEY"
TEMP_DIR = "storage/temp"
REPORT_DIR = "storage/reportes"
INVENTORY_PATH = "config/inventario_empresa.xlsx"
```

---

## 📤 Ejemplo de solicitud y respuesta JSON

**Solicitud POST:** `.msg`, `.docx`, `.xlsx`, `.pdf` + metadatos (fecha, remitente, responsable)

```json
{
  "tipo_analisis": "Correo / Contrato / Boletin",
  "resultado": "Sospechoso / Parcialmente Cumple / Vulnerabilidades identificadas",
  "criticidad": "Alta / Media / Baja",
  "detalle": [
    {
      "nombre": "Función de control de acceso",
      "respuesta_excel": "Sí",
      "cumple": "No",
      "explicacion": "En el contrato no se detalla ningún control de acceso específico...",
      "comentario_analista": "Corregir a 'No' según cláusula 3.2"
    },
    {
      "cve": "CVE-2026-12345",
      "producto": "Python",
      "version": "7.8",
      "severidad": "Alta",
      "aplica": true,
      "explicacion": "Esta vulnerabilidad afecta la versión 7.8 de Python que se encuentra en producción..."
    }
  ],
  "reporte": {
    "nombre": "reporte_unificado_0001.docx",
    "base64": "JVBERi0xLjQKJ..."
  }
}
```

---

## 📝 Consejos para un repositorio profesional

1. Añadir `.gitignore`:

```
venv/
__pycache__/
storage/temp/
*.pyc
```

2. Mantener **README actualizado**, claro y completo.
3. Añadir **diagrama visual** del flujo en `docs/`.
4. Incluir **archivos de ejemplo** en `examples/` para pruebas rápidas.
5. Usar **badges** para Python, FastAPI, licencia y build.
6. Mantener cada módulo **modular y documentado** con docstrings.

---

## 📄 Licencia

MIT License - ver [LICENSE](LICENSE) para más detalles.

---

## 🤝 Contribuciones

Las contribuciones son bienvenidas. Por favor, abre un issue primero para discutir los cambios que te gustaría hacer.

---

## 📧 Contacto

Para dudas o sugerencias, abre un issue en el repositorio.

---

Con esto tu repositorio estará listo para ser **clonado, entendido y ejecutado por otros desarrolladores**, mostrando un proyecto profesional y completo.
```

**¡Listo!** Solo copia y pega este código en tu archivo `README.md` y estará perfectamente formateado para GitHub.
