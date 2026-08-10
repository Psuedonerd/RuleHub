# Metadata Renaming Audit

This audit records the recursive BNGL-based metadata copy pass over `Published/`, `Examples/`, and `Tutorials/`.
For an unambiguous directory containing `metadata.yaml` and exactly one same-directory `.bngl` file, the metadata was copied to `<BNGL basename>_metadata.yaml`. Metadata contents were not modified.

## Summary

- Created **313** BNGL-named metadata copies.
- Left **112** already-correct BNGL-named metadata copies unchanged.
- Skipped **20** directories with multiple same-directory BNGL files.
- Skipped **0** directories with `metadata.yaml` but no same-directory BNGL file.
- Removed **11** ID/directory-named copies from the earlier pass because their directories have ambiguous multi-BNGL pairings.

## Created copies

| Directory | BNGL file | Created metadata copy |
|---|---|---|
| `Published/CheemalavaguJAKSTAT` | `Cheemalavagu_JAK_STAT.bngl` | `Cheemalavagu_JAK_STAT_metadata.yaml` |
| `Published/Dembo1978` | `blbr_dembo1978.bngl` | `blbr_dembo1978_metadata.yaml` |
| `Published/Dreisigmeyer2008` | `lac_operon_dreisigmeyer2008.bngl` | `lac_operon_dreisigmeyer2008_metadata.yaml` |
| `Published/Gardner2000` | `genetic_switch_gardner2000.bngl` | `genetic_switch_gardner2000_metadata.yaml` |
| `Published/Goldstein1980` | `blbr_heterogeneity_goldstein1980.bngl` | `blbr_heterogeneity_goldstein1980_metadata.yaml` |
| `Published/Harmon2017` | `antigen_pulses_harmon2017.bngl` | `antigen_pulses_harmon2017_metadata.yaml` |
| `Published/Hlavacek1999` | `steric_effects_hlavacek1999.bngl` | `steric_effects_hlavacek1999_metadata.yaml` |
| `Published/Hlavacek2001` | `kinetic_proofreading_hlavacek2001.bngl` | `kinetic_proofreading_hlavacek2001_metadata.yaml` |
| `Published/Hlavacek2018Egg` | `egg.bngl` | `egg_metadata.yaml` |
| `Published/Macken1982` | `tlbr_solution_macken1982.bngl` | `tlbr_solution_macken1982_metadata.yaml` |
| `Published/Mallela2022/Alabama` | `Alabama.bngl` | `Alabama_metadata.yaml` |
| `Published/Mitra2019/02-egfr/bnf1/InputFiles` | `egfr.bngl` | `egfr_metadata.yaml` |
| `Published/Mitra2019/03-fcerig` | `fceri_gamma2.bngl` | `fceri_gamma2_metadata.yaml` |
| `Published/Mitra2019/04-egfrnf` | `egfr_nf.bngl` | `egfr_nf_metadata.yaml` |
| `Published/Mitra2019/06-degranulation` | `model_tofit.bngl` | `model_tofit_metadata.yaml` |
| `Published/Mitra2019/07-egg` | `egg.bngl` | `egg_metadata.yaml` |
| `Published/Mitra2019/10-egfr` | `egfr_ode.bngl` | `egfr_ode_metadata.yaml` |
| `Published/Mitra2019/11-TLBR` | `tlbr.bngl` | `tlbr_metadata.yaml` |
| `Published/Mitra2019/12-TCR` | `tcr.bngl` | `tcr_metadata.yaml` |
| `Published/Mitra2019/14-receptor-nf` | `receptor_nf.bngl` | `receptor_nf_metadata.yaml` |
| `Published/Mitra2019/15-igf1r` | `IGF1R_fit_all.bngl` | `IGF1R_fit_all_metadata.yaml` |
| `Published/Mitra2019/19-raf-constraint` | `RAFi.bngl` | `RAFi_metadata.yaml` |
| `Published/Mitra2019/20-raf-constraint4` | `RAFi.bngl` | `RAFi_metadata.yaml` |
| `Published/Mitra2019/24-jnk` | `JNKmodel_180724_bnf.bngl` | `JNKmodel_180724_bnf_metadata.yaml` |
| `Published/Mitra2019/26-tcr-sens` | `tcr_sens_tofit.bngl` | `tcr_sens_tofit_metadata.yaml` |
| `Published/Mitra2019/31-elephant` | `elephant.bngl` | `elephant_metadata.yaml` |
| `Published/Mitra2019Likelihood` | `model_ground.bngl` | `model_ground_metadata.yaml` |
| `Published/Mitra2019Likelihood/problem16` | `model0_tofit.bngl` | `model0_tofit_metadata.yaml` |
| `Published/Mitra2019Likelihood/problem16_3cat` | `model0_tofit.bngl` | `model0_tofit_metadata.yaml` |
| `Published/Mitra2019Likelihood/problem32` | `model0_tofit.bngl` | `model0_tofit_metadata.yaml` |
| `Published/Mitra2019Likelihood/problem32_3cat` | `model0_tofit.bngl` | `model0_tofit_metadata.yaml` |
| `Published/Mitra2019Likelihood/problem4` | `model0_tofit.bngl` | `model0_tofit_metadata.yaml` |
| `Published/Mitra2019Likelihood/problem4_3cat` | `model0_tofit.bngl` | `model0_tofit_metadata.yaml` |
| `Published/Mitra2019Likelihood/problem64` | `model0_tofit.bngl` | `model0_tofit_metadata.yaml` |
| `Published/Mitra2019Likelihood/problem64_3cat` | `model0_tofit.bngl` | `model0_tofit_metadata.yaml` |
| `Published/Mitra2019Likelihood/problem8` | `model0_tofit.bngl` | `model0_tofit_metadata.yaml` |
| `Published/Mitra2019Likelihood/problem8_3cat` | `model0_tofit.bngl` | `model0_tofit_metadata.yaml` |
| `Published/Mitra2019Likelihood/problem_quant` | `model_tofit.bngl` | `model_tofit_metadata.yaml` |
| `Published/Ordyan2020/CaMKIIholo` | `CaMKII_holo.bngl` | `CaMKII_holo_metadata.yaml` |
| `Published/Ordyan2020/extraCaMKIIHolo` | `extra_CaMKII_Holo.bngl` | `extra_CaMKII_Holo_metadata.yaml` |
| `Published/Ordyan2020/mCaMKIICaSpike` | `mCaMKII_Ca_Spike.bngl` | `mCaMKII_Ca_Spike_metadata.yaml` |
| `Published/Posner1995` | `blbr_rings_posner1995.bngl` | `blbr_rings_posner1995_metadata.yaml` |
| `Published/Posner2004` | `blbr_cooperativity_posner2004.bngl` | `blbr_cooperativity_posner2004_metadata.yaml` |
| `Published/PyBioNetGen/HIVdynamics/pt303` | `pt303.bngl` | `pt303_metadata.yaml` |
| `Published/PyBioNetGen/HIVdynamics/pt403` | `pt403.bngl` | `pt403_metadata.yaml` |
| `Published/PyBioNetGen/HIVdynamics/pt409` | `pt409.bngl` | `pt409_metadata.yaml` |
| `Published/PyBioNetGen/core/IGF1RModelreceptoractivationbnf` | `IGF1R_Model_receptor_activation_bnf.bngl` | `IGF1R_Model_receptor_activation_bnf_metadata.yaml` |
| `Published/PyBioNetGen/core/RAFi` | `RAFi.bngl` | `RAFi_metadata.yaml` |
| `Published/PyBioNetGen/core/RAFiground` | `RAFi_ground.bngl` | `RAFi_ground_metadata.yaml` |
| `Published/PyBioNetGen/core/degranulationmodel` | `degranulation_model.bngl` | `degranulation_model_metadata.yaml` |
| `Published/PyBioNetGen/core/egfr` | `egfr.bngl` | `egfr_metadata.yaml` |
| `Published/PyBioNetGen/core/egfrground` | `egfr_ground.bngl` | `egfr_ground_metadata.yaml` |
| `Published/PyBioNetGen/core/egfrnf` | `egfr_nf.bngl` | `egfr_nf_metadata.yaml` |
| `Published/PyBioNetGen/core/egfrode` | `egfr_ode.bngl` | `egfr_ode_metadata.yaml` |
| `Published/PyBioNetGen/core/egfrode_published-models_PyBNG` | `egfr_ode.bngl` | `egfr_ode_metadata.yaml` |
| `Published/PyBioNetGen/core/example1` | `example1.bngl` | `example1_metadata.yaml` |
| `Published/PyBioNetGen/core/example2startingpoint` | `example2_starting_point.bngl` | `example2_starting_point_metadata.yaml` |
| `Published/PyBioNetGen/core/fcerigamma2` | `fceri_gamma2.bngl` | `fceri_gamma2_metadata.yaml` |
| `Published/PyBioNetGen/core/fcerigamma2groundtruth` | `fceri_gamma2_ground_truth.bngl` | `fceri_gamma2_ground_truth_metadata.yaml` |
| `Published/PyBioNetGen/core/model` | `model.bngl` | `model_metadata.yaml` |
| `Published/PyBioNetGen/core/model_Degranulation_aMCMC` | `model.bngl` | `model_metadata.yaml` |
| `Published/PyBioNetGen/core/modeltofit` | `model_tofit.bngl` | `model_tofit_metadata.yaml` |
| `Published/PyBioNetGen/core/parabola` | `parabola.bngl` | `parabola_metadata.yaml` |
| `Published/PyBioNetGen/core/parabola_demo` | `parabola.bngl` | `parabola_metadata.yaml` |
| `Published/PyBioNetGen/core/parabolaground` | `parabola_ground.bngl` | `parabola_ground_metadata.yaml` |
| `Published/PyBioNetGen/core/polynomial` | `polynomial.bngl` | `polynomial_metadata.yaml` |
| `Published/PyBioNetGen/core/polynomialground` | `polynomial_ground.bngl` | `polynomial_ground_metadata.yaml` |
| `Published/PyBioNetGen/core/receptor` | `receptor.bngl` | `receptor_metadata.yaml` |
| `Published/PyBioNetGen/core/receptornf` | `receptor_nf.bngl` | `receptor_nf_metadata.yaml` |
| `Published/PyBioNetGen/core/tcr` | `tcr.bngl` | `tcr_metadata.yaml` |
| `Published/PyBioNetGen/core/tlbr` | `tlbr.bngl` | `tlbr_metadata.yaml` |
| `Published/PyBioNetGen/tests/ErrNoFrees` | `ErrNoFrees.bngl` | `ErrNoFrees_metadata.yaml` |
| `Published/PyBioNetGen/tests/LilyIgE` | `LilyIgE.bngl` | `LilyIgE_metadata.yaml` |
| `Published/PyBioNetGen/tests/NFmodel` | `NFmodel.bngl` | `NFmodel_metadata.yaml` |
| `Published/PyBioNetGen/tests/ParamsEverywhere` | `ParamsEverywhere.bngl` | `ParamsEverywhere_metadata.yaml` |
| `Published/PyBioNetGen/tests/Simple` | `Simple.bngl` | `Simple_metadata.yaml` |
| `Published/PyBioNetGen/tests/SimpleAddActions` | `Simple_AddActions.bngl` | `Simple_AddActions_metadata.yaml` |
| `Published/PyBioNetGen/tests/SimpleAnswer` | `Simple_Answer.bngl` | `Simple_Answer_metadata.yaml` |
| `Published/PyBioNetGen/tests/SimpleGenOnly` | `Simple_GenOnly.bngl` | `Simple_GenOnly_metadata.yaml` |
| `Published/PyBioNetGen/tests/Simplenogen` | `Simple_nogen.bngl` | `Simple_nogen_metadata.yaml` |
| `Published/PyBioNetGen/tests/Tricky` | `Tricky.bngl` | `Tricky_metadata.yaml` |
| `Published/PyBioNetGen/tests/TrickyUS` | `TrickyUS.bngl` | `TrickyUS_metadata.yaml` |
| `Published/PyBioNetGen/tests/actionssyntax` | `actions_syntax.bngl` | `actions_syntax_metadata.yaml` |
| `Published/PyBioNetGen/tests/bngerror` | `bng_error.bngl` | `bng_error_metadata.yaml` |
| `Published/PyBioNetGen/tests/egg` | `egg.bngl` | `egg_metadata.yaml` |
| `Published/PyBioNetGen/tests/freemissing` | `free_missing.bngl` | `free_missing_metadata.yaml` |
| `Published/PyBioNetGen/tests/nofrees` | `no_frees.bngl` | `no_frees_metadata.yaml` |
| `Published/PyBioNetGen/tests/nogeneratenetwork` | `no_generate_network.bngl` | `no_generate_network_metadata.yaml` |
| `Published/PyBioNetGen/tests/nosuffix` | `no_suffix.bngl` | `no_suffix_metadata.yaml` |
| `Published/PyBioNetGen/tests/parabola` | `parabola.bngl` | `parabola_metadata.yaml` |
| `Published/PyBioNetGen/tests/parabola2` | `parabola2.bngl` | `parabola2_metadata.yaml` |
| `Published/PyBioNetGen/tests/parabola_bngl_files` | `parabola.bngl` | `parabola_metadata.yaml` |
| `Published/PyBioNetGen/tests/parabola_bngl_files_special_cases_model_check` | `parabola.bngl` | `parabola_metadata.yaml` |
| `Published/PyBioNetGen/tests/polynomial` | `polynomial.bngl` | `polynomial_metadata.yaml` |
| `Published/PyBioNetGen/tests/polynomial_full_tests_T6-check` | `polynomial.bngl` | `polynomial_metadata.yaml` |
| `Published/PyBioNetGen/tests/receptornf` | `receptor_nf.bngl` | `receptor_nf_metadata.yaml` |
| `Published/PyBioNetGen/tests/simplenfseed` | `simple_nf_seed.bngl` | `simple_nf_seed_metadata.yaml` |
| `Published/PyBioNetGen/tests/trivial` | `trivial.bngl` | `trivial_metadata.yaml` |
| `Published/Salazar-Cavazos2019/PyBNF-fitting-setup` | `190127_CHO_EGFR_forBNF.bngl` | `190127_CHO_EGFR_forBNF_metadata.yaml` |
| `Published/Thomas2016/example1_BNFfiles` | `example1.bngl` | `example1_metadata.yaml` |
| `Published/Thomas2016/example2_BNFfiles` | `example2.bngl` | `example2_metadata.yaml` |
| `Published/Thomas2016/example3_BNFfiles` | `example3.bngl` | `example3_metadata.yaml` |
| `Published/Thomas2016/example4_BNFfiles` | `example4.bngl` | `example4_metadata.yaml` |
| `Published/Thomas2016/example5_BNFfiles` | `example5.bngl` | `example5_metadata.yaml` |
| `Published/Thomas2016/example6_BNFfiles` | `example6.bngl` | `example6_metadata.yaml` |
| `Published/VaxAndVariants/Dallas` | `Dallas.bngl` | `Dallas_metadata.yaml` |
| `Published/VaxAndVariants/Houston` | `Houston.bngl` | `Houston_metadata.yaml` |
| `Published/VaxAndVariants/NYC` | `NYC.bngl` | `NYC_metadata.yaml` |
| `Published/VaxAndVariants/Phoenix` | `Phoenix.bngl` | `Phoenix_metadata.yaml` |
| `Published/Yang2008` | `tlbr_yang2008.bngl` | `tlbr_yang2008_metadata.yaml` |
| `Examples/biology/ampksignaling` | `ampk-signaling.bngl` | `ampk-signaling_metadata.yaml` |
| `Examples/biology/apoptosiscascade` | `apoptosis-cascade.bngl` | `apoptosis-cascade_metadata.yaml` |
| `Examples/biology/autoactivationloop` | `auto-activation-loop.bngl` | `auto-activation-loop_metadata.yaml` |
| `Examples/biology/bcrsignaling` | `bcr-signaling.bngl` | `bcr-signaling_metadata.yaml` |
| `Examples/biology/bistabletoggleswitch` | `bistable-toggle-switch.bngl` | `bistable-toggle-switch_metadata.yaml` |
| `Examples/biology/bmpsignaling` | `bmp-signaling.bngl` | `bmp-signaling_metadata.yaml` |
| `Examples/biology/calcineurinnfatpathway` | `calcineurin-nfat-pathway.bngl` | `calcineurin-nfat-pathway_metadata.yaml` |
| `Examples/biology/calciumspikesignaling` | `calcium-spike-signaling.bngl` | `calcium-spike-signaling_metadata.yaml` |
| `Examples/biology/chemotaxissignaltransduction` | `chemotaxis-signal-transduction.bngl` | `chemotaxis-signal-transduction_metadata.yaml` |
| `Examples/biology/circadianoscillator` | `circadian-oscillator.bngl` | `circadian-oscillator_metadata.yaml` |
| `Examples/biology/clockbmal1genecircuit` | `clock-bmal1-gene-circuit.bngl` | `clock-bmal1-gene-circuit_metadata.yaml` |
| `Examples/biology/egfrsignalingpathway` | `egfr-signaling-pathway.bngl` | `egfr-signaling-pathway_metadata.yaml` |
| `Examples/biology/eif2astressresponse` | `eif2a-stress-response.bngl` | `eif2a-stress-response_metadata.yaml` |
| `Examples/biology/endosomalsortingrab` | `endosomal-sorting-rab.bngl` | `endosomal-sorting-rab_metadata.yaml` |
| `Examples/biology/erknucleartranslocation` | `erk-nuclear-translocation.bngl` | `erk-nuclear-translocation_metadata.yaml` |
| `Examples/biology/erstressresponse` | `er-stress-response.bngl` | `er-stress-response_metadata.yaml` |
| `Examples/biology/fgfsignalingpathway` | `fgf-signaling-pathway.bngl` | `fgf-signaling-pathway_metadata.yaml` |
| `Examples/biology/gas6axlsignaling` | `gas6-axl-signaling.bngl` | `gas6-axl-signaling_metadata.yaml` |
| `Examples/biology/geneexpressiontoggle` | `gene-expression-toggle.bngl` | `gene-expression-toggle_metadata.yaml` |
| `Examples/biology/glioblastomaegfrviiisignaling` | `glioblastoma-egfrviii-signaling.bngl` | `glioblastoma-egfrviii-signaling_metadata.yaml` |
| `Examples/biology/glycolysisbranchpoint` | `glycolysis-branch-point.bngl` | `glycolysis-branch-point_metadata.yaml` |
| `Examples/biology/gpcrdesensitizationarrestin` | `gpcr-desensitization-arrestin.bngl` | `gpcr-desensitization-arrestin_metadata.yaml` |
| `Examples/biology/hedgehogsignalingpathway` | `hedgehog-signaling-pathway.bngl` | `hedgehog-signaling-pathway_metadata.yaml` |
| `Examples/biology/hematopoieticgrowthfactor` | `hematopoietic-growth-factor.bngl` | `hematopoietic-growth-factor_metadata.yaml` |
| `Examples/biology/hif1adegradationloop` | `hif1a_degradation_loop.bngl` | `hif1a_degradation_loop_metadata.yaml` |
| `Examples/biology/hypoxiaresponsesignaling` | `hypoxia-response-signaling.bngl` | `hypoxia-response-signaling_metadata.yaml` |
| `Examples/biology/il1bsignaling` | `il1b-signaling.bngl` | `il1b-signaling_metadata.yaml` |
| `Examples/biology/il6jakstatpathway` | `il6-jak-stat-pathway.bngl` | `il6-jak-stat-pathway_metadata.yaml` |
| `Examples/biology/immunesynapseformation` | `immune-synapse-formation.bngl` | `immune-synapse-formation_metadata.yaml` |
| `Examples/biology/inflammasomeactivation` | `inflammasome-activation.bngl` | `inflammasome-activation_metadata.yaml` |
| `Examples/biology/inositolphosphatemetabolism` | `inositol-phosphate-metabolism.bngl` | `inositol-phosphate-metabolism_metadata.yaml` |
| `Examples/biology/insulinglucosehomeostasis` | `insulin-glucose-homeostasis.bngl` | `insulin-glucose-homeostasis_metadata.yaml` |
| `Examples/biology/lipidmediatedpip3signaling` | `lipid-mediated-pip3-signaling.bngl` | `lipid-mediated-pip3-signaling_metadata.yaml` |
| `Examples/biology/ltypecalciumchanneldynamics` | `l-type-calcium-channel-dynamics.bngl` | `l-type-calcium-channel-dynamics_metadata.yaml` |
| `Examples/biology/mapksignalingcascade` | `mapk-signaling-cascade.bngl` | `mapk-signaling-cascade_metadata.yaml` |
| `Examples/biology/quorumsensingcircuit` | `quorum-sensing-circuit.bngl` | `quorum-sensing-circuit_metadata.yaml` |
| `Examples/biology/stat3mediatedtranscription` | `stat3-mediated-transcription.bngl` | `stat3-mediated-transcription_metadata.yaml` |
| `Examples/biology/stressresponseadaptation` | `stress-response-adaptation.bngl` | `stress-response-adaptation_metadata.yaml` |
| `Examples/biology/synapticplasticityltp` | `synaptic-plasticity-ltp.bngl` | `synaptic-plasticity-ltp_metadata.yaml` |
| `Examples/biology/tcellactivation` | `t-cell-activation.bngl` | `t-cell-activation_metadata.yaml` |
| `Examples/biology/tlr3dsrnasensing` | `tlr3-dsrna-sensing.bngl` | `tlr3-dsrna-sensing_metadata.yaml` |
| `Examples/biology/tnfinducedapoptosis` | `tnf-induced-apoptosis.bngl` | `tnf-induced-apoptosis_metadata.yaml` |
| `Examples/biology/twocomponentsystem` | `two-component-system.bngl` | `two-component-system_metadata.yaml` |
| `Examples/biology/vegfangiogenesis` | `vegf-angiogenesis.bngl` | `vegf-angiogenesis_metadata.yaml` |
| `Examples/biology/viralsensinginnateimmunity` | `viral-sensing-innate-immunity.bngl` | `viral-sensing-innate-immunity_metadata.yaml` |
| `Examples/biology/wntbetacateninsignaling` | `wnt-beta-catenin-signaling.bngl` | `wnt-beta-catenin-signaling_metadata.yaml` |
| `Examples/biology/woundhealingpdgfsignaling` | `wound-healing-pdgf-signaling.bngl` | `wound-healing-pdgf-signaling_metadata.yaml` |
| `Examples/compartments/compartmentendocytosis` | `compartment_endocytosis.bngl` | `compartment_endocytosis_metadata.yaml` |
| `Examples/compartments/compartmentmembranebound` | `compartment_membrane_bound.bngl` | `compartment_membrane_bound_metadata.yaml` |
| `Examples/compartments/compartmentnestedtransport` | `compartment_nested_transport.bngl` | `compartment_nested_transport_metadata.yaml` |
| `Examples/compartments/compartmentnucleartransport` | `compartment_nuclear_transport.bngl` | `compartment_nuclear_transport_metadata.yaml` |
| `Examples/compartments/compartmentorganelleexchange` | `compartment_organelle_exchange.bngl` | `compartment_organelle_exchange_metadata.yaml` |
| `Examples/cs/csdiffiehellman` | `cs_diffie_hellman.bngl` | `cs_diffie_hellman_metadata.yaml` |
| `Examples/cs/cshashfunction` | `cs_hash_function.bngl` | `cs_hash_function_metadata.yaml` |
| `Examples/cs/cshuffman` | `cs_huffman.bngl` | `cs_huffman_metadata.yaml` |
| `Examples/cs/csmontecarlopi` | `cs_monte_carlo_pi.bngl` | `cs_monte_carlo_pi_metadata.yaml` |
| `Examples/cs/cspagerank` | `cs_pagerank.bngl` | `cs_pagerank_metadata.yaml` |
| `Examples/cs/cspidcontroller` | `cs_pid_controller.bngl` | `cs_pid_controller_metadata.yaml` |
| `Examples/cs/csregexnfa` | `cs_regex_nfa.bngl` | `cs_regex_nfa_metadata.yaml` |
| `Examples/ecology/ecocoevolutionhostparasite` | `eco_coevolution_host_parasite.bngl` | `eco_coevolution_host_parasite_metadata.yaml` |
| `Examples/ecology/ecofoodwebchaos3sp` | `eco_food_web_chaos_3sp.bngl` | `eco_food_web_chaos_3sp_metadata.yaml` |
| `Examples/ecology/ecolotkavolterragrid` | `eco_lotka_volterra_grid.bngl` | `eco_lotka_volterra_grid_metadata.yaml` |
| `Examples/ecology/ecomutualismobligate` | `eco_mutualism_obligate.bngl` | `eco_mutualism_obligate_metadata.yaml` |
| `Examples/ecology/ecorockpaperscissorsspatial` | `eco_rock_paper_scissors_spatial.bngl` | `eco_rock_paper_scissors_spatial_metadata.yaml` |
| `Examples/energy/energyallosterymwc` | `energy_allostery_mwc.bngl` | `energy_allostery_mwc_metadata.yaml` |
| `Examples/energy/energycatalysismm` | `energy_catalysis_mm.bngl` | `energy_catalysis_mm_metadata.yaml` |
| `Examples/energy/energycooperativityadh` | `energy_cooperativity_adh.bngl` | `energy_cooperativity_adh_metadata.yaml` |
| `Examples/energy/energylinearchain` | `energy_linear_chain.bngl` | `energy_linear_chain_metadata.yaml` |
| `Examples/energy/energytransportpump` | `energy_transport_pump.bngl` | `energy_transport_pump_metadata.yaml` |
| `Examples/feature-demos/featurefunctionalratesvolume` | `feature_functional_rates_volume.bngl` | `feature_functional_rates_volume_metadata.yaml` |
| `Examples/feature-demos/featureglobalfunctionsscan` | `feature_global_functions_scan.bngl` | `feature_global_functions_scan_metadata.yaml` |
| `Examples/feature-demos/featurelocalfunctionsexplicit` | `feature_local_functions_explicit.bngl` | `feature_local_functions_explicit_metadata.yaml` |
| `Examples/feature-demos/featuresymmetryfactorscyclic` | `feature_symmetry_factors_cyclic.bngl` | `feature_symmetry_factors_cyclic_metadata.yaml` |
| `Examples/feature-demos/featuresynthesisdegradationss` | `feature_synthesis_degradation_ss.bngl` | `feature_synthesis_degradation_ss_metadata.yaml` |
| `Examples/generative/gmgameoflife` | `gm_game_of_life.bngl` | `gm_game_of_life_metadata.yaml` |
| `Examples/generative/gmraymarcher` | `gm_ray_marcher.bngl` | `gm_ray_marcher_metadata.yaml` |
| `Examples/genetics/geneticbistabilityenergy` | `genetic_bistability_energy.bngl` | `genetic_bistability_energy_metadata.yaml` |
| `Examples/genetics/geneticdnareplicationstochastic` | `genetic_dna_replication_stochastic.bngl` | `genetic_dna_replication_stochastic_metadata.yaml` |
| `Examples/genetics/geneticgoodwinoscillator` | `genetic_goodwin_oscillator.bngl` | `genetic_goodwin_oscillator_metadata.yaml` |
| `Examples/genetics/genetictranslationkinetics` | `genetic_translation_kinetics.bngl` | `genetic_translation_kinetics_metadata.yaml` |
| `Examples/genetics/geneticturingpattern1d` | `genetic_turing_pattern_1d.bngl` | `genetic_turing_pattern_1d_metadata.yaml` |
| `Examples/meta/metaformalgametheory` | `meta_formal_game_theory.bngl` | `meta_formal_game_theory_metadata.yaml` |
| `Examples/meta/metaformalmolecularclock` | `meta_formal_molecular_clock.bngl` | `meta_formal_molecular_clock_metadata.yaml` |
| `Examples/meta/metaformalpetrinet` | `meta_formal_petri_net.bngl` | `meta_formal_petri_net_metadata.yaml` |
| `Examples/meta/mtarithmeticcompiler` | `mt_arithmetic_compiler.bngl` | `mt_arithmetic_compiler_metadata.yaml` |
| `Examples/meta/mtbnglinterpreter` | `mt_bngl_interpreter.bngl` | `mt_bngl_interpreter_metadata.yaml` |
| `Examples/meta/mtmusicsequencer` | `mt_music_sequencer.bngl` | `mt_music_sequencer_metadata.yaml` |
| `Examples/meta/mtpascaltriangle` | `mt_pascal_triangle.bngl` | `mt_pascal_triangle_metadata.yaml` |
| `Examples/meta/mtquine` | `mt_quine.bngl` | `mt_quine_metadata.yaml` |
| `Examples/ml/mlgradientdescent` | `ml_gradient_descent.bngl` | `ml_gradient_descent_metadata.yaml` |
| `Examples/ml/mlhopfield` | `ml_hopfield.bngl` | `ml_hopfield_metadata.yaml` |
| `Examples/ml/mlkmeans` | `ml_kmeans.bngl` | `ml_kmeans_metadata.yaml` |
| `Examples/ml/mlqlearning` | `ml_q_learning.bngl` | `ml_q_learning_metadata.yaml` |
| `Examples/ml/mlsvm` | `ml_svm.bngl` | `ml_svm_metadata.yaml` |
| `Examples/ml/nnxor` | `nn_xor.bngl` | `nn_xor_metadata.yaml` |
| `Examples/nfsim/nfsimcoarsegraining` | `nfsim_coarse_graining.bngl` | `nfsim_coarse_graining_metadata.yaml` |
| `Examples/nfsim/nfsimdynamiccompartments` | `nfsim_dynamic_compartments.bngl` | `nfsim_dynamic_compartments_metadata.yaml` |
| `Examples/nfsim/nfsimringclosurepolymer` | `nfsim_ring_closure_polymer.bngl` | `nfsim_ring_closure_polymer_metadata.yaml` |
| `Examples/physics/phlorenzattractor` | `ph_lorenz_attractor.bngl` | `ph_lorenz_attractor_metadata.yaml` |
| `Examples/physics/phnbodygravity` | `ph_nbody_gravity.bngl` | `ph_nbody_gravity_metadata.yaml` |
| `Examples/physics/phschrodinger` | `ph_schrodinger.bngl` | `ph_schrodinger_metadata.yaml` |
| `Examples/physics/phwaveequation` | `ph_wave_equation.bngl` | `ph_wave_equation_metadata.yaml` |
| `Examples/processes/processactintreadmilling` | `process_actin_treadmilling.bngl` | `process_actin_treadmilling_metadata.yaml` |
| `Examples/processes/processautophagyflux` | `process_autophagy_flux.bngl` | `process_autophagy_flux_metadata.yaml` |
| `Examples/processes/processcelladhesionstrength` | `process_cell_adhesion_strength.bngl` | `process_cell_adhesion_strength_metadata.yaml` |
| `Examples/processes/processkineticproofreadingtcr` | `process_kinetic_proofreading_tcr.bngl` | `process_kinetic_proofreading_tcr_metadata.yaml` |
| `Examples/processes/processquorumsensingswitch` | `process_quorum_sensing_switch.bngl` | `process_quorum_sensing_switch_metadata.yaml` |
| `Examples/signal-processing/spfouriersynthesizer` | `sp_fourier_synthesizer.bngl` | `sp_fourier_synthesizer_metadata.yaml` |
| `Examples/signal-processing/spimageconvolution` | `sp_image_convolution.bngl` | `sp_image_convolution_metadata.yaml` |
| `Examples/signal-processing/spkalmanfilter` | `sp_kalman_filter.bngl` | `sp_kalman_filter_metadata.yaml` |
| `Examples/synbio/synbiobandpassfilter` | `synbio_band_pass_filter.bngl` | `synbio_band_pass_filter_metadata.yaml` |
| `Examples/synbio/synbiocountermolecular` | `synbio_counter_molecular.bngl` | `synbio_counter_molecular_metadata.yaml` |
| `Examples/synbio/synbioedgedetector` | `synbio_edge_detector.bngl` | `synbio_edge_detector_metadata.yaml` |
| `Examples/synbio/synbiologicgatesenzymatic` | `synbio_logic_gates_enzymatic.bngl` | `synbio_logic_gates_enzymatic_metadata.yaml` |
| `Examples/synbio/synbiooscillatorsynchronization` | `synbio_oscillator_synchronization.bngl` | `synbio_oscillator_synchronization_metadata.yaml` |
| `Examples/wacky/wackyalchemystone` | `wacky_alchemy_stone.bngl` | `wacky_alchemy_stone_metadata.yaml` |
| `Examples/wacky/wackyblackhole` | `wacky_black_hole.bngl` | `wacky_black_hole_metadata.yaml` |
| `Examples/wacky/wackybouncingball` | `wacky_bouncing_ball.bngl` | `wacky_bouncing_ball_metadata.yaml` |
| `Examples/wacky/wackytrafficjamasep` | `wacky_traffic_jam_asep.bngl` | `wacky_traffic_jam_asep_metadata.yaml` |
| `Examples/wacky/wackyzombieinfection` | `wacky_zombie_infection.bngl` | `wacky_zombie_infection_metadata.yaml` |
| `Tutorials/CaOscillateFunc` | `CaOscillate_Func.bngl` | `CaOscillate_Func_metadata.yaml` |
| `Tutorials/CaOscillateSat` | `CaOscillate_Sat.bngl` | `CaOscillate_Sat_metadata.yaml` |
| `Tutorials/General/polymerdraft` | `polymer_draft.bngl` | `polymer_draft_metadata.yaml` |
| `Tutorials/General/quasiequilibrium` | `quasi_equilibrium.bngl` | `quasi_equilibrium_metadata.yaml` |
| `Tutorials/General/simple` | `simple.bngl` | `simple_metadata.yaml` |
| `Tutorials/Haugh2b` | `Haugh2b.bngl` | `Haugh2b_metadata.yaml` |
| `Tutorials/Kiefhaberemodel` | `Kiefhaber_emodel.bngl` | `Kiefhaber_emodel_metadata.yaml` |
| `Tutorials/Motivatingexample` | `Motivating_example.bngl` | `Motivating_example_metadata.yaml` |
| `Tutorials/MotivatingexamplecBNGL` | `Motivating_example_cBNGL.bngl` | `Motivating_example_cBNGL_metadata.yaml` |
| `Tutorials/NativeTutorials/AB` | `AB.bngl` | `AB_metadata.yaml` |
| `Tutorials/NativeTutorials/ABC` | `ABC.bngl` | `ABC_metadata.yaml` |
| `Tutorials/NativeTutorials/ABCscan` | `ABC_scan.bngl` | `ABC_scan_metadata.yaml` |
| `Tutorials/NativeTutorials/ABCssa` | `ABC_ssa.bngl` | `ABC_ssa_metadata.yaml` |
| `Tutorials/NativeTutorials/ABp` | `ABp.bngl` | `ABp_metadata.yaml` |
| `Tutorials/NativeTutorials/ABpapprox` | `ABp_approx.bngl` | `ABp_approx_metadata.yaml` |
| `Tutorials/NativeTutorials/BAB` | `BAB.bngl` | `BAB_metadata.yaml` |
| `Tutorials/NativeTutorials/BABcoop` | `BAB_coop.bngl` | `BAB_coop_metadata.yaml` |
| `Tutorials/NativeTutorials/BABscan` | `BAB_scan.bngl` | `BAB_scan_metadata.yaml` |
| `Tutorials/NativeTutorials/BLBR` | `BLBR.bngl` | `BLBR_metadata.yaml` |
| `Tutorials/NativeTutorials/Chyleklibrary` | `Chylek_library.bngl` | `Chylek_library_metadata.yaml` |
| `Tutorials/NativeTutorials/CircadianOscillator` | `CircadianOscillator.bngl` | `CircadianOscillator_metadata.yaml` |
| `Tutorials/NativeTutorials/ComplexDegradation` | `ComplexDegradation.bngl` | `ComplexDegradation_metadata.yaml` |
| `Tutorials/NativeTutorials/Creamer2012` | `Creamer_2012.bngl` | `Creamer_2012_metadata.yaml` |
| `Tutorials/NativeTutorials/FceRIji` | `FceRI_ji.bngl` | `FceRI_ji_metadata.yaml` |
| `Tutorials/NativeTutorials/FceRIviz` | `FceRI_viz.bngl` | `FceRI_viz_metadata.yaml` |
| `Tutorials/NativeTutorials/GK` | `GK.bngl` | `GK_metadata.yaml` |
| `Tutorials/NativeTutorials/LR` | `LR.bngl` | `LR_metadata.yaml` |
| `Tutorials/NativeTutorials/LRR` | `LRR.bngl` | `LRR_metadata.yaml` |
| `Tutorials/NativeTutorials/LRRcomp` | `LRR_comp.bngl` | `LRR_comp_metadata.yaml` |
| `Tutorials/NativeTutorials/LRcomp` | `LR_comp.bngl` | `LR_comp_metadata.yaml` |
| `Tutorials/NativeTutorials/LV` | `LV.bngl` | `LV_metadata.yaml` |
| `Tutorials/NativeTutorials/LVcomp` | `LV_comp.bngl` | `LV_comp_metadata.yaml` |
| `Tutorials/NativeTutorials/Lisman` | `Lisman.bngl` | `Lisman_metadata.yaml` |
| `Tutorials/NativeTutorials/Lismanbifurcate` | `Lisman_bifurcate.bngl` | `Lisman_bifurcate_metadata.yaml` |
| `Tutorials/NativeTutorials/Repressilator` | `Repressilator.bngl` | `Repressilator_metadata.yaml` |
| `Tutorials/NativeTutorials/SIR` | `SIR.bngl` | `SIR_metadata.yaml` |
| `Tutorials/NativeTutorials/Suderman2013` | `Suderman_2013.bngl` | `Suderman_2013_metadata.yaml` |
| `Tutorials/NativeTutorials/birthdeath` | `birth-death.bngl` | `birth-death_metadata.yaml` |
| `Tutorials/NativeTutorials/cBNGLsimple` | `cBNGL_simple.bngl` | `cBNGL_simple_metadata.yaml` |
| `Tutorials/NativeTutorials/egfrsimple` | `egfr_simple.bngl` | `egfr_simple_metadata.yaml` |
| `Tutorials/NativeTutorials/organelletransport` | `organelle_transport.bngl` | `organelle_transport_metadata.yaml` |
| `Tutorials/NativeTutorials/organelletransportstruct` | `organelle_transport_struct.bngl` | `organelle_transport_struct_metadata.yaml` |
| `Tutorials/NativeTutorials/toggle` | `toggle.bngl` | `toggle_metadata.yaml` |
| `Tutorials/NativeTutorials/translateSBML` | `translateSBML.bngl` | `translateSBML_metadata.yaml` |
| `Tutorials/NativeTutorials/visualize` | `visualize.bngl` | `visualize_metadata.yaml` |
| `Tutorials/SHP2basemodel` | `SHP2_base_model.bngl` | `SHP2_base_model_metadata.yaml` |
| `Tutorials/catalysis` | `catalysis.bngl` | `catalysis_metadata.yaml` |
| `Tutorials/continue` | `continue.bngl` | `continue_metadata.yaml` |
| `Tutorials/egfrnet` | `egfr_net.bngl` | `egfr_net_metadata.yaml` |
| `Tutorials/egfrnetred` | `egfr_net_red.bngl` | `egfr_net_red_metadata.yaml` |
| `Tutorials/egfrpath` | `egfr_path.bngl` | `egfr_path_metadata.yaml` |
| `Tutorials/energyexample1` | `energy_example1.bngl` | `energy_example1_metadata.yaml` |
| `Tutorials/example1` | `example1.bngl` | `example1_metadata.yaml` |
| `Tutorials/fcerijicomp` | `fceri_ji_comp.bngl` | `fceri_ji_comp_metadata.yaml` |
| `Tutorials/heise` | `heise.bngl` | `heise_metadata.yaml` |
| `Tutorials/issue198short` | `issue_198_short.bngl` | `issue_198_short_metadata.yaml` |
| `Tutorials/localfunc` | `localfunc.bngl` | `localfunc_metadata.yaml` |
| `Tutorials/michment` | `michment.bngl` | `michment_metadata.yaml` |
| `Tutorials/michmentcont` | `michment_cont.bngl` | `michment_cont_metadata.yaml` |
| `Tutorials/motor` | `motor.bngl` | `motor_metadata.yaml` |
| `Tutorials/mwc` | `mwc.bngl` | `mwc_metadata.yaml` |
| `Tutorials/nfkb` | `nfkb.bngl` | `nfkb_metadata.yaml` |
| `Tutorials/nfkbillustratingprotocols` | `nfkb_illustrating_protocols.bngl` | `nfkb_illustrating_protocols_metadata.yaml` |
| `Tutorials/polymerfixed` | `polymer_fixed.bngl` | `polymer_fixed_metadata.yaml` |
| `Tutorials/recdim` | `rec_dim.bngl` | `rec_dim_metadata.yaml` |
| `Tutorials/recdimcomp` | `rec_dim_comp.bngl` | `rec_dim_comp_metadata.yaml` |
| `Tutorials/simplenfsimtest` | `simple_nfsim_test.bngl` | `simple_nfsim_test_metadata.yaml` |
| `Tutorials/simplesbmlimport` | `simple_sbml_import.bngl` | `simple_sbml_import_metadata.yaml` |
| `Tutorials/simplesystem` | `simple_system.bngl` | `simple_system_metadata.yaml` |
| `Tutorials/testANGsynthesissimple` | `test_ANG_synthesis_simple.bngl` | `test_ANG_synthesis_simple_metadata.yaml` |
| `Tutorials/testMM` | `test_MM.bngl` | `test_MM_metadata.yaml` |
| `Tutorials/testfixed` | `test_fixed.bngl` | `test_fixed_metadata.yaml` |
| `Tutorials/testmratio` | `test_mratio.bngl` | `test_mratio_metadata.yaml` |
| `Tutorials/testnetworkgen` | `test_network_gen.bngl` | `test_network_gen_metadata.yaml` |
| `Tutorials/testsat` | `test_sat.bngl` | `test_sat_metadata.yaml` |
| `Tutorials/testsynthesiscBNGLsimple` | `test_synthesis_cBNGL_simple.bngl` | `test_synthesis_cBNGL_simple_metadata.yaml` |
| `Tutorials/testsynthesiscomplex` | `test_synthesis_complex.bngl` | `test_synthesis_complex_metadata.yaml` |
| `Tutorials/testsynthesiscomplex0cBNGL` | `test_synthesis_complex_0_cBNGL.bngl` | `test_synthesis_complex_0_cBNGL_metadata.yaml` |
| `Tutorials/testsynthesiscomplexsourcecBNGL` | `test_synthesis_complex_source_cBNGL.bngl` | `test_synthesis_complex_source_cBNGL_metadata.yaml` |
| `Tutorials/testsynthesissimple` | `test_synthesis_simple.bngl` | `test_synthesis_simple_metadata.yaml` |
| `Tutorials/tlmr` | `tlmr.bngl` | `tlmr_metadata.yaml` |
| `Tutorials/toyjim` | `toy-jim.bngl` | `toy-jim_metadata.yaml` |
| `Tutorials/univsynth` | `univ_synth.bngl` | `univ_synth_metadata.yaml` |

## Already correct (unchanged)

| Directory | BNGL file | Existing metadata copy |
|---|---|---|
| `Published/An2009` | `An_2009.bngl` | `An_2009_metadata.yaml` |
| `Published/Barua2007` | `Barua_2007.bngl` | `Barua_2007_metadata.yaml` |
| `Published/Barua2009` | `Barua_2009.bngl` | `Barua_2009_metadata.yaml` |
| `Published/Barua2013` | `Barua_2013.bngl` | `Barua_2013_metadata.yaml` |
| `Published/BaruaBCR2012` | `BaruaBCR_2012.bngl` | `BaruaBCR_2012_metadata.yaml` |
| `Published/BaruaFceRI2012` | `BaruaFceRI_2012.bngl` | `BaruaFceRI_2012_metadata.yaml` |
| `Published/Blinov2006` | `Blinov_2006.bngl` | `Blinov_2006_metadata.yaml` |
| `Published/Blinovegfr` | `Blinov_egfr.bngl` | `Blinov_egfr_metadata.yaml` |
| `Published/Blinovran` | `Blinov_ran.bngl` | `Blinov_ran_metadata.yaml` |
| `Published/Chattaraj2021` | `Chattaraj_2021.bngl` | `Chattaraj_2021_metadata.yaml` |
| `Published/ChylekFceRI2014` | `ChylekFceRI_2014.bngl` | `ChylekFceRI_2014_metadata.yaml` |
| `Published/ChylekTCR2014` | `ChylekTCR_2014.bngl` | `ChylekTCR_2014_metadata.yaml` |
| `Published/Dolan2015` | `Dolan_2015.bngl` | `Dolan_2015_metadata.yaml` |
| `Published/Dushek2011` | `Dushek_2011.bngl` | `Dushek_2011_metadata.yaml` |
| `Published/Dushek2014` | `Dushek_2014.bngl` | `Dushek_2014_metadata.yaml` |
| `Published/Erdem2021` | `Erdem_2021.bngl` | `Erdem_2021_metadata.yaml` |
| `Published/Hat2016` | `Hat_2016.bngl` | `Hat_2016_metadata.yaml` |
| `Published/JaruszewiczBlonska2023` | `Jaruszewicz-Blonska_2023.bngl` | `Jaruszewicz-Blonska_2023_metadata.yaml` |
| `Published/Jung2017` | `Jung_2017.bngl` | `Jung_2017_metadata.yaml` |
| `Published/Kesseler2013` | `Kesseler_2013.bngl` | `Kesseler_2013_metadata.yaml` |
| `Published/Kocieniewski2012` | `Kocieniewski_2012.bngl` | `Kocieniewski_2012_metadata.yaml` |
| `Published/Korwek2023` | `Korwek_2023.bngl` | `Korwek_2023_metadata.yaml` |
| `Published/Kozer2013` | `Kozer_2013.bngl` | `Kozer_2013_metadata.yaml` |
| `Published/Kozer2014` | `Kozer_2014.bngl` | `Kozer_2014_metadata.yaml` |
| `Published/Lang2024` | `Lang_2024.bngl` | `Lang_2024_metadata.yaml` |
| `Published/Ligon2014` | `Ligon_2014.bngl` | `Ligon_2014_metadata.yaml` |
| `Published/LinERK2019` | `Lin_ERK_2019.bngl` | `Lin_ERK_2019_metadata.yaml` |
| `Published/LinPrion2019` | `Lin_Prion_2019.bngl` | `Lin_Prion_2019_metadata.yaml` |
| `Published/LinTCR2019` | `Lin_TCR_2019.bngl` | `Lin_TCR_2019_metadata.yaml` |
| `Published/Massole2023` | `Massole_2023.bngl` | `Massole_2023_metadata.yaml` |
| `Published/McMillan2021` | `McMillan_2021.bngl` | `McMillan_2021_metadata.yaml` |
| `Published/Mertins2023` | `Mertins_2023.bngl` | `Mertins_2023_metadata.yaml` |
| `Published/ModelZAP` | `Model_ZAP.bngl` | `Model_ZAP_metadata.yaml` |
| `Published/Mukhopadhyay2013` | `Mukhopadhyay_2013.bngl` | `Mukhopadhyay_2013_metadata.yaml` |
| `Published/MyrtleBeachConwayNorthMyrtleBeachSCNC` | `Myrtle_Beach-Conway-North_Myrtle_Beach_SC-NC.bngl` | `Myrtle_Beach-Conway-North_Myrtle_Beach_SC-NC_metadata.yaml` |
| `Published/Nag2009` | `Nag_2009.bngl` | `Nag_2009_metadata.yaml` |
| `Published/Nosbisch2022` | `Nosbisch_2022.bngl` | `Nosbisch_2022_metadata.yaml` |
| `Published/Pekalski2013` | `Pekalski_2013.bngl` | `Pekalski_2013_metadata.yaml` |
| `Published/RulebasedRantransport` | `Rule_based_Ran_transport.bngl` | `Rule_based_Ran_transport_metadata.yaml` |
| `Published/RulebasedRantransportdraft` | `Rule_based_Ran_transport_draft.bngl` | `Rule_based_Ran_transport_draft_metadata.yaml` |
| `Published/Rulebasedegfrcompart` | `Rule_based_egfr_compart.bngl` | `Rule_based_egfr_compart_metadata.yaml` |
| `Published/Rulebasedegfrtutorial` | `Rule_based_egfr_tutorial.bngl` | `Rule_based_egfr_tutorial_metadata.yaml` |
| `Published/Zhang2021` | `Zhang_2021.bngl` | `Zhang_2021_metadata.yaml` |
| `Published/Zhang2023` | `Zhang_2023.bngl` | `Zhang_2023_metadata.yaml` |
| `Published/fcerifyn` | `fceri_fyn.bngl` | `fceri_fyn_metadata.yaml` |
| `Published/innateimmunity` | `innate_immunity.bngl` | `innate_immunity_metadata.yaml` |
| `Published/mapkdimers` | `mapk-dimers.bngl` | `mapk-dimers_metadata.yaml` |
| `Published/mapkmonomers` | `mapk-monomers.bngl` | `mapk-monomers_metadata.yaml` |
| `Published/notch` | `notch.bngl` | `notch_metadata.yaml` |
| `Published/tlbr` | `tlbr.bngl` | `tlbr_metadata.yaml` |
| `Published/vilar2002` | `vilar_2002.bngl` | `vilar_2002_metadata.yaml` |
| `Published/vilar2002b` | `vilar_2002b.bngl` | `vilar_2002b_metadata.yaml` |
| `Published/vilar2002c` | `vilar_2002c.bngl` | `vilar_2002c_metadata.yaml` |
| `Published/wnt` | `wnt.bngl` | `wnt_metadata.yaml` |
| `Examples/biology/aktsignaling` | `akt-signaling.bngl` | `akt-signaling_metadata.yaml` |
| `Examples/biology/allostericactivation` | `allosteric-activation.bngl` | `allosteric-activation_metadata.yaml` |
| `Examples/biology/autophagyregulation` | `autophagy-regulation.bngl` | `autophagy-regulation_metadata.yaml` |
| `Examples/biology/betaadrenergicresponse` | `beta-adrenergic-response.bngl` | `beta-adrenergic-response_metadata.yaml` |
| `Examples/biology/bloodcoagulationthrombin` | `blood-coagulation-thrombin.bngl` | `blood-coagulation-thrombin_metadata.yaml` |
| `Examples/biology/brusselatoroscillator` | `brusselator-oscillator.bngl` | `brusselator-oscillator_metadata.yaml` |
| `Examples/biology/caspaseactivationloop` | `caspase-activation-loop.bngl` | `caspase-activation-loop_metadata.yaml` |
| `Examples/biology/cd40signaling` | `cd40-signaling.bngl` | `cd40-signaling_metadata.yaml` |
| `Examples/biology/cellcyclecheckpoint` | `cell-cycle-checkpoint.bngl` | `cell-cycle-checkpoint_metadata.yaml` |
| `Examples/biology/checkpointkinasesignaling` | `checkpoint-kinase-signaling.bngl` | `checkpoint-kinase-signaling_metadata.yaml` |
| `Examples/biology/competitiveenzymeinhibition` | `competitive-enzyme-inhibition.bngl` | `competitive-enzyme-inhibition_metadata.yaml` |
| `Examples/biology/complementactivationcascade` | `complement-activation-cascade.bngl` | `complement-activation-cascade_metadata.yaml` |
| `Examples/biology/contactinhibitionhippoyap` | `contact-inhibition-hippo-yap.bngl` | `contact-inhibition-hippo-yap_metadata.yaml` |
| `Examples/biology/cooperativebinding` | `cooperative-binding.bngl` | `cooperative-binding_metadata.yaml` |
| `Examples/biology/dnadamagerepair` | `dna-damage-repair.bngl` | `dna-damage-repair_metadata.yaml` |
| `Examples/biology/dnamethylationdynamics` | `dna-methylation-dynamics.bngl` | `dna-methylation-dynamics_metadata.yaml` |
| `Examples/biology/dr5apoptosissignaling` | `dr5-apoptosis-signaling.bngl` | `dr5-apoptosis-signaling_metadata.yaml` |
| `Examples/biology/dualsitephosphorylation` | `dual-site-phosphorylation.bngl` | `dual-site-phosphorylation_metadata.yaml` |
| `Examples/biology/e2frbcellcycleswitch` | `e2f-rb-cell-cycle-switch.bngl` | `e2f-rb-cell-cycle-switch_metadata.yaml` |
| `Examples/biology/interferonsignaling` | `interferon-signaling.bngl` | `interferon-signaling_metadata.yaml` |
| `Examples/biology/ire1axbp1erstress` | `ire1a-xbp1-er-stress.bngl` | `ire1a-xbp1-er-stress_metadata.yaml` |
| `Examples/biology/jakstatcytokinesignaling` | `jak-stat-cytokine-signaling.bngl` | `jak-stat-cytokine-signaling_metadata.yaml` |
| `Examples/biology/jnkmapksignaling` | `jnk-mapk-signaling.bngl` | `jnk-mapk-signaling_metadata.yaml` |
| `Examples/biology/kirchannelregulation` | `kir-channel-regulation.bngl` | `kir-channel-regulation_metadata.yaml` |
| `Examples/biology/lacoperonregulation` | `lac-operon-regulation.bngl` | `lac-operon-regulation_metadata.yaml` |
| `Examples/biology/michaelismentenkinetics` | `michaelis-menten-kinetics.bngl` | `michaelis-menten-kinetics_metadata.yaml` |
| `Examples/biology/mtorc2signaling` | `mtorc2-signaling.bngl` | `mtorc2-signaling_metadata.yaml` |
| `Examples/biology/mtorsignaling` | `mtor-signaling.bngl` | `mtor-signaling_metadata.yaml` |
| `Examples/biology/myogenicdifferentiation` | `myogenic-differentiation.bngl` | `myogenic-differentiation_metadata.yaml` |
| `Examples/biology/negativefeedbackloop` | `negative-feedback-loop.bngl` | `negative-feedback-loop_metadata.yaml` |
| `Examples/biology/neurotransmitterrelease` | `neurotransmitter-release.bngl` | `neurotransmitter-release_metadata.yaml` |
| `Examples/biology/nfkbfeedback` | `nfkb-feedback.bngl` | `nfkb-feedback_metadata.yaml` |
| `Examples/biology/nocgmpsignaling` | `no-cgmp-signaling.bngl` | `no-cgmp-signaling_metadata.yaml` |
| `Examples/biology/notchdeltalateralinhibition` | `notch-delta-lateral-inhibition.bngl` | `notch-delta-lateral-inhibition_metadata.yaml` |
| `Examples/biology/oxidativestressresponse` | `oxidative-stress-response.bngl` | `oxidative-stress-response_metadata.yaml` |
| `Examples/biology/p38mapksignaling` | `p38-mapk-signaling.bngl` | `p38-mapk-signaling_metadata.yaml` |
| `Examples/biology/p53mdm2oscillator` | `p53-mdm2-oscillator.bngl` | `p53-mdm2-oscillator_metadata.yaml` |
| `Examples/biology/parp1mediateddnarepair` | `parp1-mediated-dna-repair.bngl` | `parp1-mediated-dna-repair_metadata.yaml` |
| `Examples/biology/phosphorelaychain` | `phosphorelay-chain.bngl` | `phosphorelay-chain_metadata.yaml` |
| `Examples/biology/plateletactivation` | `platelet-activation.bngl` | `platelet-activation_metadata.yaml` |
| `Examples/biology/predatorpreydynamics` | `predator-prey-dynamics.bngl` | `predator-prey-dynamics_metadata.yaml` |
| `Examples/biology/rabgtpasecycle` | `rab-gtpase-cycle.bngl` | `rab-gtpase-cycle_metadata.yaml` |
| `Examples/biology/ranklranksignaling` | `rankl-rank-signaling.bngl` | `rankl-rank-signaling_metadata.yaml` |
| `Examples/biology/rasgefgapcycle` | `ras-gef-gap-cycle.bngl` | `ras-gef-gap-cycle_metadata.yaml` |
| `Examples/biology/repressilatoroscillator` | `repressilator-oscillator.bngl` | `repressilator-oscillator_metadata.yaml` |
| `Examples/biology/retinoicacidsignaling` | `retinoic-acid-signaling.bngl` | `retinoic-acid-signaling_metadata.yaml` |
| `Examples/biology/rhogtpaseactincytoskeleton` | `rho-gtpase-actin-cytoskeleton.bngl` | `rho-gtpase-actin-cytoskeleton_metadata.yaml` |
| `Examples/biology/shp2phosphataseregulation` | `shp2-phosphatase-regulation.bngl` | `shp2-phosphatase-regulation_metadata.yaml` |
| `Examples/biology/signalamplificationcascade` | `signal-amplification-cascade.bngl` | `signal-amplification-cascade_metadata.yaml` |
| `Examples/biology/simpledimerization` | `simple-dimerization.bngl` | `simple-dimerization_metadata.yaml` |
| `Examples/biology/sirepidemicmodel` | `sir-epidemic-model.bngl` | `sir-epidemic-model_metadata.yaml` |
| `Examples/biology/smadtgfbetasignaling` | `smad-tgf-beta-signaling.bngl` | `smad-tgf-beta-signaling_metadata.yaml` |
| `Examples/biology/sonichedgehoggradient` | `sonic-hedgehog-gradient.bngl` | `sonic-hedgehog-gradient_metadata.yaml` |
| `Examples/nfsim/nfsimhybridparticlefield` | `nfsim_hybrid_particle_field.bngl` | `nfsim_hybrid_particle_field_metadata.yaml` |
| `Tutorials/General/chemistry` | `chemistry.bngl` | `chemistry_metadata.yaml` |
| `Tutorials/General/polymer` | `polymer.bngl` | `polymer_metadata.yaml` |
| `Tutorials/General/toy1` | `toy1.bngl` | `toy1_metadata.yaml` |
| `Tutorials/General/toy2` | `toy2.bngl` | `toy2_metadata.yaml` |

## Ambiguous directories (skipped)

No new metadata copy was created in these directories because one `metadata.yaml` could not be paired unambiguously with a single BNGL file.

| Directory | BNGL count |
|---|---:|
| `Published/Faeder2003` | 2 |
| `Published/Hlavacek2018Elephant` | 2 |
| `Published/Hlavacek2018Restructuration` | 7 |
| `Published/Lin2019` | 3 |
| `Published/Mallela2021` | 50 |
| `Published/Mallela2021_Cities` | 15 |
| `Published/Mallela2022_MSAs` | 281 |
| `Published/Miller2022_NavajoNation` | 5 |
| `Published/Miller2025_MEK` | 10 |
| `Published/Mitra2019/02-egfr` | 2 |
| `Published/Mitra2019/05-threestep` | 2 |
| `Published/Mitra2019/13-receptor` | 2 |
| `Published/Mitra2019/17-egfr-ssa` | 2 |
| `Published/Mitra2019/18-mapk` | 2 |
| `Published/Mitra2019/28-mapk` | 2 |
| `Published/Mitra2019/30-jobs` | 2 |
| `Published/Mitra2019Rab` | 4 |
| `Published/Mitra2019Rab/pybnf_files` | 4 |
| `Published/Salazar-Cavazos2019` | 7 |
| `Published/Thomas2016` | 7 |

## Earlier ambiguous copies removed

| Removed file | Reason |
|---|---|
| `Published/Hlavacek2018Elephant/Hlavacek_2018_Elephant_metadata.yaml` | Parent directory contains multiple BNGL files. |
| `Published/Hlavacek2018Restructuration/Hlavacek_2018_Restructuration_metadata.yaml` | Parent directory contains multiple BNGL files. |
| `Published/Lin2019/Lin_2019_metadata.yaml` | Parent directory contains multiple BNGL files. |
| `Published/Mallela2021/Mallela_2021_metadata.yaml` | Parent directory contains multiple BNGL files. |
| `Published/Mallela2021_Cities/Mallela2021_Cities_metadata.yaml` | Parent directory contains multiple BNGL files. |
| `Published/Mallela2022_MSAs/Mallela2022_MSAs_metadata.yaml` | Parent directory contains multiple BNGL files. |
| `Published/Miller2022_NavajoNation/Miller2022_NavajoNation_metadata.yaml` | Parent directory contains multiple BNGL files. |
| `Published/Miller2025_MEK/Miller2025_MEK_metadata.yaml` | Parent directory contains multiple BNGL files. |
| `Published/Mitra2019Rab/Mitra_2019_Rab_metadata.yaml` | Parent directory contains multiple BNGL files. |
| `Published/Salazar-Cavazos2019/Salazar-Cavazos_2019_metadata.yaml` | Parent directory contains multiple BNGL files. |
| `Published/Thomas2016/Thomas_2016_metadata.yaml` | Parent directory contains multiple BNGL files. |

## Directories without a same-directory BNGL file (skipped)

None.
