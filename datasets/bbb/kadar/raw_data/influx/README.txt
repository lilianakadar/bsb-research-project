ChEMBL query

-------------INFLUX QUERY: SLC22A5, SLC47A1, SLCO1A2, SLCO2B1, SLCO1C1, MBOAT1, MBOAT2, MBOAT4, SLC7A5 ------------

SELECT activities.molregno, activities.pchembl_value, compound_structures.canonical_smiles, component_sequences.accession
FROM activities
JOIN assays ON assays.assay_id = activities.assay_id
JOIN target_components ON target_components.tid = assays.tid
JOIN component_sequences ON component_sequences.component_id = target_components.component_id
JOIN compound_structures ON activities.molregno = compound_structures.molregno
WHERE component_sequences.accession IN ('O76082','Q96FL8','P46721','094956','Q9NYB5','Q6ZNC8','Q6ZWT7','Q96T53','Q01650')
  AND activities.pchembl_value IS NOT NULL
  AND activities.data_validity_comment IS NULL
  AND activities.potential_duplicate = 0;
