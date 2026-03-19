# Provider Column Dictionary

- provider_name: ClearPoint Care
- provider_folder: data_provider_4_clearpoint_care
- upload_partition: dt=2026-03-19

## patients

- `CLI_ID`: Patient/customer identifier from legacy source. (canonical: `PT_001_ID`)
- `G_CODE`: Gender code from source domain. (canonical: `GDR_CD`)
- `B_DATE`: Birth date in mixed source formats. (canonical: `BDT_VAL`)
- `REC_STS`: Legacy status code using obfuscated enums. (canonical: `REC_STS`)

## encounters

- `EKEY`: Encounter identifier in source system. (canonical: `ENC_KEY`)
- `PT_REF`: Patient reference in child tables. (canonical: `PT_REF`)
- `EVT_DTTM`: Encounter date in mixed source formats. (canonical: `ENC_DT_RAW`)
- `ACT_FLAG`: Legacy status code using obfuscated enums. (canonical: `REC_STS`)

## conditions

- `DX_KEY`: Condition record identifier. (canonical: `CND_KEY`)
- `PARENT_PT`: Patient reference in child tables. (canonical: `PT_REF`)
- `ENC_REF`: Encounter reference in dependent tables. (canonical: `ENC_REF`)
- `DX_CODE`: Condition hint code similar to ICD. (canonical: `ICD_HINT`)
- `ACT_FLAG`: Legacy status code using obfuscated enums. (canonical: `REC_STS`)

## medications

- `PRESC_ID`: Medication order identifier. (canonical: `MED_KEY`)
- `PT_LINK`: Patient reference in child tables. (canonical: `PT_REF`)
- `VISIT_REF`: Encounter reference in dependent tables. (canonical: `ENC_REF`)
- `ORD_DATE`: Medication order date in mixed formats. (canonical: `ORD_DT_RAW`)
- `STS_CD`: Legacy status code using obfuscated enums. (canonical: `REC_STS`)

## observations

- `OBS_REF`: Observation record identifier. (canonical: `OBS_KEY`)
- `PT_LINK`: Patient reference in child tables. (canonical: `PT_REF`)
- `E_REF`: Encounter reference in dependent tables. (canonical: `ENC_REF`)
- `OBS_DT_RAW`: Observation date in mixed source formats. (canonical: `OBS_DT_RAW`)
- `OBS_PAYLOAD`: Nested JSON payload with inconsistent shape. (canonical: `OBS_PAYLOAD`)
- `ROW_STS`: Legacy status code using obfuscated enums. (canonical: `REC_STS`)
