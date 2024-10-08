<template>
  <TextContent title='DESIGN'
               :title-list="['Overview', 'Dataset', 'Structure Prediction', 'Evaluation Metrics', 'Subcellular Localization Prediction', 'Protein Directed Evolution Model']">
    <h1 id='Overview'>Overview</h1>
    <p>Atlas.Y consists of a main functional pathway and several auxiliary features. The core function of the software
      is the <span class='bold'>design of localization proteins</span>, utilizing the <span class='bold'>signal
      dataset</span> and <span class='bold'>linker dataset</span>, along with <span class='bold'>structural prediction
      algorithms</span> and <span class='bold'>functional stability scoring algorithms</span>, to provide users with
      appropriate signal sequences and linker sequences for their proteins, thereby enhancing the success rate of
      subcellular localization.</p>
    <p>In addition, Atlas.Y includes various auxiliary algorithms, such as the <span class='bold'>Site-Specific CAD
      Scoring System, Protein Localization Prediction System, Optimized Protein Evolution Localization System, and
      Temporal Dynamic Localization Design System</span>, aimed at offering users a richer and more comprehensive
      experience.</p>

    <h1 id='Dataset'>Dataset</h1>
    <h4>Signal Peptide Dataset</h4>
    <p>Our Signal Peptide Dataset is designed to facilitate research on protein subcellular localization and transport.
      Signal peptides are short sequences located at the N-terminus of newly synthesized proteins, responsible for
      determining the subcellular localization of these proteins. The data in this dataset is sourced from the dataset
      used in the development of the <span class='bold'>DeepLoc 2.1</span> deep learning model by Marius Thrane Ødum et
      al. To align with the goals of our project, we specifically filtered the dataset to include only proteins from
      eukaryotic organisms, extracted the signal peptides, categorized them, and assigned unique identifiers to enable
      efficient querying. This dataset is particularly suitable for bioinformatics research, protein design, and cell
      biology experiments focused on predicting subcellular localization.</p>
    <img src='https://static.igem.wiki/teams/5503/accompanying-images/design1-1.webp' alt='Design1'>
    <h5>Figure. Atlas.Y: Signal Peptide Dataset fragment display</h5>
    <h4>Linker Dataset</h4>
    <p>We aim to construct a linker dataset designed to connect our target proteins with signal peptide sequences. The
      dataset is divided into two tables: the Classical Linker Data Table and the Natural Linker Data Table.</p>
    <ol>
      <li><span class='bold'>Classical Linker Table</span>: This section contains linkers that have been extensively
        reviewed in the literature and categorized based on their rigidity and flexibility. The linker sequences in this
        table are suitable for use in protein design, molecular biology, and synthetic biology engineering projects.
      </li>
      <img src='https://static.igem.wiki/teams/5503/accompanying-images/design2-1.webp' alt='Design2'>
      <h5>Figure. Atlas.Y: Classical Linker Dataset fragment display</h5>
      <li><span class='bold'>Natural Linker Table</span>: This section consists of short peptides derived from natural
        protein sequences without artificial optimization. These natural linkers are generated by removing signal
        peptides and conserved regions, following the method used by the 2021 Sun Yat-sen University iGEM team. We used
        protein sequences from the DeepLoc 2.1 dataset, and identified conserved regions using NCBI's Conserved Domain
        Database (CDD) and its Batch CD-Search tool.
      </li>
      <img src='https://static.igem.wiki/teams/5503/accompanying-images/design3-1.webp' alt='Design3'>
      <h5>Figure. Atlas.Y: Natural Linker Dataset fragment display</h5>
    </ol>
    <p>Building on this hypothesis, we employed the ESMFold model to predict the three-dimensional structures of all
      linkers and calculated their average B-factors. To validate the effectiveness of the B-factor as a measure of
      rigidity and flexibility, we conducted a t-test on the classical linkers obtained from the literature. The results
      demonstrated a significant difference between the average B-factors and the rigidity classifications, yielding a
      p-value of <span class='bold'>6.145×10<sup>-14</sup></span>, which confirms that the B-factor can indeed serve as
      a reliable indicator of linker rigidity and flexibility.</p>
    <p>Based on this finding, we subsequently classified the natural linkers extracted from proteins according to their
      rigidity and flexibility, thereby addressing the varying experimental requirements for linker flexibility.</p>
    <p>In order to explore the properties of linkers, we also calculated their <span class='bold'>hydrophobicity</span>
      to assess their <span class='bold'>suitability</span> in different biological environments. This process utilized
      the ProteinAnalysis class from the <span class='bold'>Bio.SeqUtils.ProtParam</span> module. By analyzing the
      linker sequences, we can obtain hydrophilic and hydrophobic indices, which will provide additional reference
      points for selecting appropriate linkers in experimental designs.</p>
    <h4>Photocontrolled Protein Interaction Localization Database (PPID)</h4>
    <p><span class='bold'>Optogenetics</span> is an emerging biotechnological approach that utilizes light-sensitive
      proteins and specific wavelengths of light to precisely regulate the functions and interactions of proteins within
      cells. This method enables researchers to achieve high spatial and temporal resolution control in live cells,
      facilitating a deeper understanding of cellular behaviors and physiological processes.</p>
    <img src='https://static.igem.wiki/teams/5503/accompanying-images/design4-1.webp' alt='Design4'>
    <h5>Figure. Atlas.Y: Optogenetic protein pairs used in Atlas.Y</h5>
    <p>In constructing the PPID Database, we conducted extensive literature research to ensure the efficacy and
      applicability of the selected optogenetic systems.</p>
    <p>The information regarding the blue light-induced optogenetic pair <span class='bold'>CIBN-CRY2</span> system is
      derived from the study by Kennedy et al., titled "Rapid blue-light-mediated induction of protein interactions in
      living cells" The research indicates that this system exhibits a faster response time and greater flexibility
      compared to the original <span class='bold'>CIB1</span>, thereby allowing for real-time regulation of protein
      interactions.</p>
    <p>For the red light-induced <span class='bold'>PhyB-PIF3</span> system, we referenced the study by Konrad Müller et
      al., titled "A red/far-red light-responsive bi-stable toggle switch to control gene expression in mammalian cells"
      This system demonstrates good reversibility, enabling protein binding under red light induction and separation
      under far-red light induction, thus allowing reversible gene regulation.</p>
    <p>Additionally, concerning the near-infrared light-controlled optogenetic pair, we referenced the research by
      Kaberniuk et al., titled "A bacterial phytochrome-based optogenetic system controllable with near-infrared light".
      The proposed single-domain <span class='bold'>BphP1</span> binding partner <span class='bold'>Q-PAS1</span>
      effectively overcomes the limitations posed by the large size, multi-domain structure, and oligomerization
      behavior of the traditional BphP1-PpsR2 system.</p>
    <p>To visualize the subcellular localization behaviors of different optogenetic pairs and their spectral
      multiplexing capabilities, we selected three pairs of fluorescent proteins with high color contrast from the
      <span class='bold'>GenBank</span> database for labeling. These fluorescent proteins are as follows:</p>
    <ul>
      <li>Red fluorescent protein <span class='bold'>mCherry</span> (UFQ89828.1) and green fluorescent protein
        <span class='bold'>eGFP</span> (UYB79189.1)
      </li>
      <li>Blue fluorescent protein <span class='bold'>mTagBFP</span> (UFQ89829.1) and orange fluorescent protein
        <span class='bold'>mKO</span> (ADE48842.1)
      </li>
      <li>Purple fluorescent protein <span class='bold'>mKate</span> (WKV34671.1) and yellow fluorescent protein
        <span class='bold'>mVenus</span> (AWK40018.1)
      </li>
    </ul>
    <p>The PPID Database is built upon existing signal peptide and linker databases. For each specific subcellular
      localization, we arrange and combine the corresponding signal peptide and linker data, linking them with the
      optogenetic proteins and fluorescent proteins. Subsequently, we utilize the built-in stability calculation methods
      in <span class='bold'>PyRosetta</span> to evaluate the stability of the resulting fusion proteins, ultimately
      storing the combinations with the <span class='bold'>highest stability</span> in our database.</p>
    <p>Through this systematic process, the PPID Database not only provides researchers with a powerful tool to explore
      the applications of optogenetics in cell biology, but also offers a wealth of data resources and experimental
      foundations for future research.</p>

    <h1 id='Structure Prediction'>Structure Prediction</h1>
    <p>In our project's design process, protein structure prediction is crucial, directly influencing the evaluation of
      fusion protein function and stability. To ensure the designed fusion proteins meet functional expectations, we
      compared several prediction tools and, after considering accuracy, speed, and resource demands, chose
      <span class='bold'>ESMFold.</span></p>
    <p>ESMFold stands out by using the ESM-2 language model to predict 3D protein structures from single sequences. This
      allows it to efficiently handle large sequences without relying on multiple sequence alignments (MSA), greatly
      reducing computational time and complexity. Its architecture, with 48 layers of the "Folding Trunk" and a
      structure module, processes sequence features to deliver accurate structural predictions.</p>
    <p>By quickly generating high-quality pdb files, ESMFold enables us to immediately assess fusion protein
      functionality and stability, significantly streamlining our workflow. This efficiency has allowed us to focus on
      optimizing designs without structural prediction bottlenecks, accelerating the entire project.</p>

    <h1 id='Evaluation Metrics'>Evaluation Metrics</h1>
    <h4>Stability Evaluation</h4>
    <p>In the Atlas.Y platform, we design fusion proteins that can be precisely localized to specific subcellular sites
      for our users. To achieve this goal, we need to add signal peptides and linkers to the proteins provided by users,
      thereby constructing protein assemblies. However, the introduction of any additional sequences may impact the
      functionality of the original proteins. Therefore, we developed the CAD (<span class='bold'>Contact Area
      Difference</span>) model to evaluate the <span class='bold'>functional changes</span> in fusion proteins.
    </p>
    <p>The design of the CAD model is based on a deep understanding of the relationship between protein structure and
      function. <span class='bold'>Contact area</span> is a crucial metric for assessing protein interactions, and by
      calculating changes in contact area, we can reflect the structural differences between the fusion proteins and
      their original counterparts. To accomplish this, we utilize <span class='bold'>Voronoi</span> diagrams and convex
      hull algorithms. We first generate a Voronoi diagram that assigns each atom in the protein structure to its
      respective spatial region, representing the influence area of that atom. This approach allows us to gain a clearer
      understanding of the role of each atom within the structure.Next, we employ the convex hull algorithm to compute
      the contact area between residues. This algorithm accurately reflects the contact regions between residues by
      determining the smallest convex polygon that encompasses the Voronoi regions.</p>
    <p>To comprehensively assess the functional changes in proteins, the CAD model not only calculates overall area
      differences but also allows for localized evaluations, focusing on <span class='bold'>specific functional
      regions</span>. This design enables researchers to gain deeper insights into the changes in interactions near
      active sites or functional domains, aiding in the assessment of how these changes impact protein functionality.
    </p>
    <p>Through this integrated design approach, the CAD model provides us with an effective tool to ensure that while
      pursuing target localization, we maximize the retention of the original protein's biological activity.</p>
    <h4>Functional Evaluation</h4>
    <p>When designing fusion proteins that can be precisely localized to specific subcellular sites for our users, we
      incorporate signal peptides and linkers into the target proteins. However, ensuring that the resulting fusion
      proteins exhibit good <span class='bold'>stability</span> is crucial, as it directly impacts the
      <span class='bold'>functionality</span> and <span class='bold'>structural</span> integrity of the proteins. To
      achieve this goal, we employ the Python-based PyRosetta interface in conjunction with the powerful Rosetta
      software suite to assess the stability of fusion proteins.</p>
    <p>During the stability evaluation process, <span class='bold'>PyRosetta</span> scoring functions take into account
      multiple factors, including van der Waals forces, electrostatic interactions, and hydrogen bonds, to calculate the
      total energy of the fusion proteins. A lower energy score indicates greater structural stability, reflecting the
      potential of fusion proteins to maintain structural integrity, functional efficiency, and prolonged lifespan. By
      integrating PyRosetta into our model, we provide users with a reliable stability assessment, ensuring that the
      designed fusion proteins not only localize accurately but also maintain their structural stability, thus
      facilitating more precise applications in bioengineering.</p>

    <h1 id='Subcellular Localization Prediction'>Subcellular Localization Prediction</h1>
    <p>We have locally deployed the <span class='bold'>DeepLoc 2.0</span> release developed by Marius Thrane Ødum et al.
      This model is capable of predicting the subcellular localization of proteins containing signal peptides and
      classifying them into <span class='bold'>ten</span> distinct cellular compartments: cytoplasm, nucleus,
      extracellular space, plasma membrane, mitochondria, plastids, endoplasmic reticulum, lysosome / vacuole, Golgi
      apparatus, and peroxisome. The model relies solely on sequence information and demonstrates exceptional
      performance, which is attributed to the use of a large, well-curated dataset that includes annotations for
      multi-localizing proteins. Additionally, a smaller dataset containing sorting signals has been used to further
      enhance the interpretability of the attention layers within the model.</p>
    <p>With this model, we can further predict the localization efficiency of the fusion proteins we design for our
      users. This predictive capability allows us to <span class='bold'>validate</span> the effectiveness of the fusion
      proteins at their target subcellular locations, thereby improving the accuracy of localization. By integrating the
      predictions from DeepLoc 2.0, we ensure that the fusion proteins provided to users not only possess the desired
      functionality but also effectively localize to the intended cellular compartments. This provides robust validation
      for our design efforts.</p>
    <img src='https://static.igem.wiki/teams/5503/accompanying-images/design5-1.webp' alt='Design5'>

    <h1 id='Protein Directed Evolution Model'>Protein Directed Evolution Model</h1>
    <p>Considering the complex protein sorting mechanisms within yeast, relying solely on signal sequence connections
      may not ensure accurate subcellular localization. The localization of many proteins depends not only on specific
      signal sequences but also on their <span class='bold'>folding states</span> and <span class='bold'>
      microenvironments</span>. Different organelles possess unique membrane characteristics and transport mechanisms,
      necessitating precise selection and adjustment of proteins before they reach their destinations.</p>
    <p>However, our current algorithms <span class='bold'>do not</span> take spatial structural features into account,
      limiting their applicability in complex environments. Therefore, combining <span class='bold'>spatial structural
      characteristics</span> related to organelle localization with sequence features can significantly enhance
      localization efficiency. For example, specialized protein complexes on the mitochondrial inner membrane not only
      recognize signal sequences but also modulate functions based on the three-dimensional conformations of proteins.
      This sensitivity to spatial structure can effectively improve the selectivity and transport efficiency of
      proteins.</p>
    <p>To integrate these spatial structural features, we have chosen the <span class='bold'>ProtLGN</span> model based
      on <span class='bold'>graph neural networks</span>, embedding proteins in the form of graphs. This approach fully
      considers the biochemical properties and spatial structures of proteins, allowing the model to take into account
      the synergistic effects of signal sequences and spatial conformations when predicting and optimizing protein
      localization. By utilizing this method, we can capture both the sequence and spatial structural features of
      proteins, providing a comprehensive understanding of their behavior in various cellular environments.</p>
    <p>We apply <span class='bold'>transfer learning</span> to fine-tune the ProtLGN model using datasets from classic
      localization proteins. This fine-tuning process enables the model to adapt to specific organelle characteristics,
      allowing it to learn the intricate details necessary for precise protein localization. The integration of sequence
      information and spatial information is crucial for the model to recognize the subtle microenvironmental factors
      that influence protein classification and localization.</p>
    <p>This comprehensive approach will assist us in designing targeting strategies with higher accuracy, advancing the
      fields of protein engineering and synthetic biology. Ultimately, our goal is to achieve efficient and precise
      protein localization across different organelles, providing strong support for related research and applications.
    </p>
  </TextContent>
</template>

<script setup lang='ts'>
import TextContent from '@/components/TextContent.vue'
</script>

<style scoped>
@import '@/styles/style.css';

img {
  width: 700px;
}
</style>
