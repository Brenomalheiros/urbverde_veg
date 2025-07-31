### 🌱Pipeline de Produção dos dados da Camada de Vegetação e Impermeabilização - URBVERDE

Este repositório contém scripts desenvolvidos no [Google Earth Engine (GEE)](https://earthengine.google.com/) para produzir mapas e indicadores de cobertura vegetal, superfícies impermeáveis e densidade populacional em áreas urbanas.

## 🎯 Objetivo

Criar uma base de dados geoespaciais para avaliação ambiental urbana, especialmente focada em:

- Mapeamento da vegetação urbana e impermeabilização.
- Interpolação das populações intraurbanas.
- Geração de indicadores ambientais agregados por setores censitários, bairros, municípios e praças.
- Exportação de rasters e métricas em formatos abertos (CSV, GeoTIFF).

---

## 📁 Estrutura dos Scripts

### 🛰️ Pré-processamento e Exportação de Rasters

| Script | Descrição |
|--------|-----------|
| `200-Export_raster_MLME-PCV-Landsat` | Exporta rasters de frações espectrais (MLME) e componentes principais (PCV) com **Landsat**. |
| `200-Export_raster_MLME-PCV-Sentinel` | Versão equivalente usando **Sentinel-2**. |
| `200-Export_raster_NDVI` | Calcula e exporta o **NDVI** (índice de vegetação). |
| `200-Export_raster_PSI` | Calcula e exporta o **PSI** (índice de selamento/permeabilização). |

### 👥 População e Dasimetria

| Script | Descrição |
|--------|-----------|
| `200-Setores_pop_interpolada` | Prepara setores censitários com população para interpolação. |
| `200-Pop_Interpolation` | Realiza interpolação da densidade populacional. |
| `201-Dasimetria_Urbana` | Calcula população intraurbana ajustada com base em áreas impermeáveis e vegetadas (dasimetria). |

### 📦 Exportações Agregadas (Índices por Polígonos)

| Script | Descrição |
|--------|-----------|
| `202-Export_PCV_PSI_setores` | Exporta médias de PCV e PSI por **setor censitário**. |
| `202-Export_PCV_PSI_bairro` | Exporta por **bairros**. |
| `202-Export_PCV_PSI_municipios` | Exporta por **municípios**. |
| `202-Export_PCV_PSI_pracas` | Exporta por **praças públicas**. |

### 🌿 Índice de Cobertura Vegetal (ICV)

| Script | Descrição |
|--------|-----------|
| `203-Export_ICV_setores` | Exporta o **ICV** por **setor censitário**. |
| `203-Export_ICV_bairro` | Exporta o **ICV** por **bairro**. |
| `203-Export_ICV_municipios` | Exporta o **ICV** por **município**. |

### 📤 Exportação Final

| Script | Descrição |
|--------|-----------|
| `207-Export_CSV` | Consolida e exporta métricas para CSV para posterior análise em R, Python ou QGIS. |

---

## 🔁 Fluxo de Processamento

1. **Pré-processamento de imagens** (Landsat/Sentinel): nuvens, correção, recorte da AOI.
2. **Cálculo de índices espectrais**: NDVI, PSI, MLME, PCV.
3. **Interpolação populacional** com base em setores censitários e dados vetoriais.
4. **Agregação por polígonos administrativos** (setores, bairros, municípios).
5. **Exportação final** para Google Drive ou Assets (GeoTIFF/CSV).

---

## 🗂️ Dados Utilizados

- Imagens Landsat 5/7/8 e Sentinel-2 MSI
- Setores censitários do IBGE
- Delimitação de bairros, praças, municípios (GeoJSON ou shapefile)
- População estimada (por setor)

---

## 🧪 Como Executar

1. Acesse o [GEE Code Editor](https://code.earthengine.google.com/).
2. Copie o código de um dos arquivos `.txt`.
3. Ajuste os seguintes parâmetros:
   - Área de interesse (`geometry`)
   - Datas (`start`, `end`)
   - Nome do asset de saída ou exportação
   - Polígonos vetoriais (caso use bairros/setores personalizados)

---

## 📊 Indicadores Gerados

- **NDVI**: índice de vegetação normalizado.
- **PSI**: índice de selamento/impermeabilização.
- **MLME**: frações espectrais de vegetação, solo, sombra.
- **PCV**: componentes principais da vegetação.
- **ICV**: proporção da cobertura vegetal sobre a área total.
- **População interpolada**: densidade ajustada intraurbanamente.
- **Dasimetria**: ajuste populacional com base em cobertura do solo.

---

## 📦 Saídas

- **GeoTIFFs**: rasters dos índices espectrais.
- **CSVs agregados**: indicadores por setor, bairro, município, praça.

---

## 📌 Aplicações

- Planejamento urbano sustentável
- Mapeamento de áreas verdes
- Monitoramento da expansão urbana
- Análise de justiça ambiental e acesso à infraestrutura verde
- Estudos populacionais intraurbanos

---

## 📄 Licença

Este projeto está licenciado sob a licença MIT. Consulte o arquivo `LICENSE` para mais detalhes.
