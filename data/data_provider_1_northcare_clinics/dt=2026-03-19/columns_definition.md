# Provider Column Dictionary

- provider_name: NorthCare Clinics
- provider_folder: data_provider_1_northcare_clinics
- upload_partition: dt=2026-03-19

## patients

- `PT_001_ID`: Patient/customer identifier from legacy source. (canonical: `PT_001_ID`)
- `GDR_CD`: Gender code from source domain. (canonical: `GDR_CD`)
- `BDT_VAL`: Birth date in mixed source formats. (canonical: `BDT_VAL`)
- `REC_STS`: Legacy status code using obfuscated enums. (canonical: `REC_STS`)

## encounters

- `ENC_KEY`: Encounter identifier in source system. (canonical: `ENC_KEY`)
- `PT_REF`: Patient reference in child tables. (canonical: `PT_REF`)
- `ENC_DT_RAW`: Encounter date in mixed source formats. (canonical: `ENC_DT_RAW`)
- `REC_STS`: Legacy status code using obfuscated enums. (canonical: `REC_STS`)

## conditions

- `CND_KEY`: Condition record identifier. (canonical: `CND_KEY`)
- `PT_REF`: Patient reference in child tables. (canonical: `PT_REF`)
- `ENC_REF`: Encounter reference in dependent tables. (canonical: `ENC_REF`)
- `ICD_HINT`: Condition hint code similar to ICD. (canonical: `ICD_HINT`)
- `REC_STS`: Legacy status code using obfuscated enums. (canonical: `REC_STS`)

## medications

- `MED_KEY`: Medication order identifier. (canonical: `MED_KEY`)
- `PT_REF`: Patient reference in child tables. (canonical: `PT_REF`)
- `ENC_REF`: Encounter reference in dependent tables. (canonical: `ENC_REF`)
- `ORD_DT_RAW`: Medication order date in mixed formats. (canonical: `ORD_DT_RAW`)
- `REC_STS`: Legacy status code using obfuscated enums. (canonical: `REC_STS`)

## observations

- `OBS_KEY`: Observation record identifier. (canonical: `OBS_KEY`)
- `PT_REF`: Patient reference in child tables. (canonical: `PT_REF`)
- `ENC_REF`: Encounter reference in dependent tables. (canonical: `ENC_REF`)
- `OBS_DT_RAW`: Observation date in mixed source formats. (canonical: `OBS_DT_RAW`)
- `OBS_PAYLOAD`: Nested JSON payload with inconsistent shape. (canonical: `OBS_PAYLOAD`)
- `REC_STS`: Legacy status code using obfuscated enums. (canonical: `REC_STS`)
