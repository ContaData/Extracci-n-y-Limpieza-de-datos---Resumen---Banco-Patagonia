Proyecto de Extracción y Limpieza de Movimientos Bancarios - BANCO PATAGONIA

Este proyecto está diseñado para automatizar la extracción, procesamiento y limpieza de datos bancarios desde extractos en formato PDF. El objetivo principal es facilitar la obtención y organización de los movimientos financieros, clasificando de manera automática las diferentes transacciones bancarias y exportándolas a archivos de Excel, donde se guardan en hojas separadas según el tipo de movimiento.

El código es capaz de procesar múltiples tipos de transacciones, incluyendo:

Movimientos de cuenta corriente y caja de ahorro
 - Plazos fijos
 - Compras con tarjetas (Visa Electrón)
 - Débitos automáticos (realizados y rechazados)
 - Transferencias recibidas y enviadas
 - Cheques pagados y rechazados
 - Saldos pendientes
La información se extrae, se limpia y luego se guarda en un archivo Excel con múltiples hojas, cada una correspondiente a un tipo de transacción.

Funcionalidades
Extracción de Datos de PDF
El script utiliza PyPDF2 para la lectura de los archivos PDF, donde busca ciertos títulos clave que definen los diferentes tipos de movimientos bancarios (como "CUENTA CORRIENTE EN PESOS" o "TRANSFERENCIAS ENVIADAS Y ACEPTADAS"). Con esta información, se identifican las páginas que contienen los datos relevantes.

Limpieza y Formato de los Datos
El módulo Tabula se utiliza para extraer las tablas de datos estructurados directamente desde las páginas de los PDFs. Luego, los datos son procesados para eliminar información irrelevante, asegurando que solo los registros válidos (como fechas y montos) sean retenidos.

Clasificación de Transacciones
El código clasifica automáticamente las transacciones en las siguientes categorías:

 - Cuenta corriente en pesos: Incluye fecha, concepto, referencia, y detalles de débito, crédito y saldo.
 - Compras con tarjeta Visa: Detalla las compras realizadas, extracciones y otros movimientos relacionados.
 - Débitos automáticos: Tanto los realizados como los rechazados.
 - Transferencias recibidas y enviadas: Clasificación de transferencias, incluyendo datos como nombre del destinatario o remitente, importe y bancos.
 - Saldos pendientes y plazos fijos: Procesa detalles de las operaciones en estas cuentas.
 - Exportación a Excel
Cada grupo de transacciones procesado se exporta a un archivo Excel utilizando pandas y xlsxwriter, generando un libro con múltiples hojas que contienen los datos limpios y organizados por tipo de transacción.

Requisitos
 - Python 3.8+
 - Librerías requeridas (instalar desde requirements.txt):
 - pandas
 - tabula-py
 - PyPDF2
 - xlsxwriter

Estructura del Proyecto

data_extraction.py: Encargado de buscar y extraer los datos relevantes de los PDFs.

data_processing.py: Procesa y limpia los datos extraídos, clasificando las transacciones.

data_export.py: Exporta los datos procesados a archivos Excel con hojas separadas por tipo de transacción.

Licencia
Este proyecto está bajo la Licencia CC BY-NC 4.0. 
Esto permite la distribución y modificación bajo ciertas condiciones, pero prohíbe el uso comercial.
