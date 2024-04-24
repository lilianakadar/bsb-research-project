ChEMBL query:

-------------EFFLUX QUERY: MDR1, BCRP, MRP1, MRP2, MRP3, MRP4, MRP5, MRP6 ------------

SELECT activities.molregno, activities.pchembl_value, compound_structures.canonical_smiles, component_sequences.accession
FROM activities
JOIN assays ON assays.assay_id = activities.assay_id
JOIN target_components ON target_components.tid = assays.tid
JOIN component_sequences ON component_sequences.component_id = target_components.component_id
JOIN compound_structures ON activities.molregno = compound_structures.molregno
WHERE component_sequences.accession IN ('P08183','Q9UNQ0','P33527','Q92887','O15438','O15439','O15440','O95255')
  AND activities.pchembl_value IS NOT NULL
  AND activities.data_validity_comment IS NULL
  AND activities.potential_duplicate = 0;