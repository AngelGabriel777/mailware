# 🛡️ Analizador Unificado de Seguridad

![Python](https://img.shields.io/badge/python-3.11-blue)
![License](https://img.shields.io/badge/license-MIT-green)

Sistema en Python para analizar automáticamente:

- Correos sospechosos (.msg)
- Contratos (Word + Excel)
- Boletines de seguridad (PDF)

Genera reportes profesionales con **IA**, evidencias y scoring de riesgo.

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
│   │   ├── parser_email.py
│   │   ├── analyzer.py
│   │   └── scorer.py
│   ├── contratos/
│   │   ├── parser_word.py
│   │   ├── parser_excel.py
│   │   ├── comparator.py
│   │   └── scorer.py
│   └── boletines/
│       ├── parser_pdf.py
│       ├── vulnerability_extractor.py
│       ├── inventory_checker.py
│       └── scorer.py
├── ai/
│   └── explanation_generator.py ← Genera texto humanizado con IA
├── reporting/
│   ├── report_generator.py      ← Word final + evidencias
│   └── templates/
│       ├── plantilla_contrato.docx
│       └── plantilla_boletin.docx
├── storage/
│   ├── temp/
│   ├── evidencias/
│   └── reportes/
├── config/
│   └── settings.example.py       ← Ejemplo de configuración
├── docs/                         ← Diagramas y documentación adicional
├── examples/                     ← Archivos de prueba (.msg, .docx, .xlsx, .pdf)
├── requirements.txt
└── README.md
