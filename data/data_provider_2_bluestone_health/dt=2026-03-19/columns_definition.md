# Provider Column Dictionary

- provider_name: BlueStone Health
- provider_folder: data_provider_2_bluestone_health
- upload_partition: dt=2026-03-19

## patients

- `CUST_ID`: Patient/customer identifier from legacy source. (canonical: `PT_001_ID`)
- `GDR_CD`: Gender code from source domain. (canonical: `GDR_CD`)
- `BDT_VAL`: Birth date in mixed source formats. (canonical: `BDT_VAL`)
- `REC_STS`: Legacy status code using obfuscated enums. (canonical: `REC_STS`)

## encounters

- `CNTCT_ID`: Encounter identifier in source system. (canonical: `ENC_KEY`)
- `PT_REF`: Patient reference in child tables. (canonical: `PT_REF`)
- `EVT_DTTM`: Encounter date in mixed source formats. (canonical: `ENC_DT_RAW`)
- `REC_STS`: Legacy status code using obfuscated enums. (canonical: `REC_STS`)

## conditions

- `COND_REF`: Condition record identifier. (canonical: `CND_KEY`)
- `PT_LINK`: Patient reference in child tables. (canonical: `PT_REF`)
- `ENC_REF`: Encounter reference in dependent tables. (canonical: `ENC_REF`)
- `DX_HINT`: Condition hint code similar to ICD. (canonical: `ICD_HINT`)
- `ROW_STS`: Legacy status code using obfuscated enums. (canonical: `REC_STS`)

## medications

- `MED_KEY`: Medication order identifier. (canonical: `MED_KEY`)
- `PARENT_PT`: Patient reference in child tables. (canonical: `PT_REF`)
- `EN_REF`: Encounter reference in dependent tables. (canonical: `ENC_REF`)
- `ORD_DT_RAW`: Medication order date in mixed formats. (canonical: `ORD_DT_RAW`)
- `ACT_FLAG`: Legacy status code using obfuscated enums. (canonical: `REC_STS`)

## observations

- `OBS_KEY`: Observation record identifier. (canonical: `OBS_KEY`)
- `CUST_REF`: Patient reference in child tables. (canonical: `PT_REF`)
- `ENC_REF`: Encounter reference in dependent tables. (canonical: `ENC_REF`)
- `MEAS_DT`: Observation date in mixed source formats. (canonical: `OBS_DT_RAW`)
- `RAW_BLOB`: Nested JSON payload with inconsistent shape. (canonical: `OBS_PAYLOAD`)
- `ROW_STS`: Legacy status code using obfuscated enums. (canonical: `REC_STS`)
