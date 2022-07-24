---
layout: page
title: Reorganization Energy Prediction
description:
---

We have 15,210 molecules in the curated QM9 dataset, where the maximum λ is about 2.94 eV.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/actc2022/qm9_distribution.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig. 1 (a) Distribution of vertical electron affinity and ionization potential, and (b) distribution of reorganization energy in the curated QM9 dataset with their mean and standard deviation
</div>

There are two different ways to predicti λ. We either (1) trained two GNNs for predicting vertical IP from neutral geometries and predicting vertical EA from cationic geometries, respectively and independently, or (2) trained one GNN to predict λ directly from rdkit geometries.

<div class="row">
    <div class="col-md-6 offset-md-3">
        {% include figure.html path="assets/img/actc2022/prediction_scheme.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig. 2 Scheme of making reorganization energy prediction by (a) predicted vertical IP from neutral geometries minus predicted vertical EA from cationic geometries (b) direct prediction of λ from RDKit geometries.
</div>

Here are the results of comparing SchNet and ChiRo for reorganization energy prediction task, where λ is from predicted vertical IP minus predicted vertical EA. ChiRo shows better generalizability on RDKit-embedded geometries though SchNet has lower error when tested on DFT optimized geometries or CREST conformers. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/actc2022/chiro_vs_sch_table.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Table 1. Performance of ChiRo vs SchNet for the reorganization energy prediction task using input geometries at different levels of theory.
</div>

We further trained and tested ChiRo using RDKit-embedded geometries and found it reaching lower error than the case of trained and tested with DFT-optimized geometries.

<div class="row">
    <div class="col-md-6 offset-md-3">
        {% include figure.html path="assets/img/actc2022/chiro_reorg_table.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Table 2. Peformance of ChiRo for reorganization energy prediction task using RDKit geometries as inputs.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/actc2022/chiro_reorg_pred.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig 3. DFT reorganization energy versus ChiRo outputs with RDKit geometries as inputs from (a) predicted vertical IP minus predicted vertical EA and (b) direct reorganization energy predictions.
</div>

