---
layout: default
---

# Single-Photon 3D Imaging with Equi-Depth Photon Histograms
<a href="https://kaustubh-sadekar.github.io/" target="_blank">Kaustubh Sadekar</a>, <a href="https://web.cecs.pdx.edu/~maier/" target="_blank">David Maier</a>, <a href="https://www.atulingle.com/" target="_blank">Atul Ingle</a>

<a href="https://arxiv.org/abs/2408.16150" target="_blank">Arxiv</a> link / <a href="https://www.ecva.net/papers/eccv_2024/papers_ECCV/html/8121_ECCV_2024_paper.php" target="_blank">ECVA</a> link / <a href="https://github.com/kaustubh-sadekar/PEDH-ECCV2024" target="_blank">Code</a> link.

# Abstract

Single-photon cameras present a promising avenue for high-resolution 3D imaging. They have ultra-high sensitivity --- down to individual photons --- and can record photon arrival times with extremely high (sub-nanosecond) resolution. Single-photon 3D cameras estimate the round-trip time of a laser pulse by forming equi-width (EW) histograms of detected photon timestamps. Acquiring and transferring such EW histograms requires high bandwidth and in-pixel memory, making SPCs less attractive in resource-constrained settings such as mobile devices and AR/VR headsets. In this work we propose a 3D sensing technique based on equi-depth (ED) histograms. ED histograms compress timestamp data more efficiently than EW histograms, reducing the bandwidth requirement. Moreover, to reduce the in-pixel memory requirement, we propose a lightweight algorithm to estimate ED histograms in an online fashion without explicitly storing the photon timestamps. This algorithm is amenable to future in-pixel implementations. We propose algorithms that process ED histograms to perform 3D computer-vision tasks of estimating scene distance maps and performing visual odometry under challenging conditions such as high ambient light. Our work paves the way towards lower bandwidth and reduced in-pixel memory requirements for SPCs, making them attractive for resource-constrained 3D vision applications.



<div style="text-align:center">

<iframe width="560" height="315" src="https://www.youtube.com/watch?v=Dwn-r2crbjY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

</div>


# Results

<div style="text-align:center">
    <img src="https://static.wixstatic.com/media/e3a603_f03f99ddeded4ca68c03ded0c3c691b1~mv2.png/v1/crop/x_136,y_0,w_6775,h_3711/fill/w_780,h_431,al_c,q_85,usm_0.66_1.00_0.01,enc_auto/Conventional_vs_Proposed_SPCs_for_3D_Vsion.png" />
</div>

> **Our proposed DeePEDH pipeline enables SPCs to be used in resource-constrained applications.** SPCs generate large amounts of raw timestamp data, requiring high in-pixel memory and causing a data bottleneck. (a-d) Conventional 3D SPCs resort to low-resolution equi-width (EW) histograms resulting in poor distance resolution. (e-g) DeePEDH uses a more efficient on-sensor compression scheme through equi-depth (ED) histograms combined with a deep neural network distance map estimator. (h) The proposed method provides accurate high-resolution distance maps with 10 - 100x lower bandwidth. (i-k) DeePEDH paves the way for various computer vision tasks to be performed on resource-constrained devices using SPCs for 3D sensing.


<div style="text-align:center">
    <img src="https://static.wixstatic.com/media/e3a603_5af53633c84a4d3ab2a2df520c85a939~mv2.png/v1/crop/x_11,y_0,w_2989,h_829/fill/w_780,h_215,al_c,q_85,usm_0.66_1.00_0.01,enc_auto/Equi-width_VS_Equi-depth_Histograms.png" />
</div>

> **Equi-width vs. equi-depth histograms for peaky data.** (a) Most bins of an 8-bin EW histogram are wasted on background photons; a single bin B2 gives a coarse estimate of the true peak. (b) An ED histogram captures this “peaky” transient distribution better with a cluster of narrower bins around the true peak.


<div style="text-align:center">
    <img src="https://static.wixstatic.com/media/e3a603_a989cc09cc4e4f1abc323faf1d59d2b2~mv2.png/v1/fill/w_780,h_280,al_c,q_85,usm_0.66_1.00_0.01,enc_auto/Improved_binner_with_optimized_stepping.png" />
</div>

> **A binner element used for tracking ED histogram boundaries.** (a) A median-finding binner splits the incident photons into early (En) and late photons (Ln) compared to Cn, the control value (CV) which is the current estimated median-value of the binner. In this case, there are more early photons than late, hence the step size Sn is negative to move the CV left. (b) Our optimized stepping strategy uses a sequence of step sizes to achieve faster convergence and lower variance compared to earlier fixed-stepping binner design.


<div style="text-align:center">
    <img src="https://static.wixstatic.com/media/e3a603_81a3864dbb6c4066b4f50999445f1a54~mv2.png/v1/fill/w_780,h_434,al_c,q_85,usm_0.66_1.00_0.01,enc_auto/Improved_Distance_Estimates_Using_DeePEDH.png" />
</div>

> **Comparison of distance map reconstructions on NYUv2 test images.** The CSPH algorithm, HEDH (narrowest bin), and the PEDH (narrowest bin) methods suffer from noisy distance maps in darker regions and scene points at farther distances. The 32-bin EWH suffers from quantization artifacts. The proposed DNN-based DeePEDH method learns the spatiotemporal correlations between the PEDH output to provide both high spatial and distance resolution even in regions where other methods fail.


<div style="text-align:center">
    <img src="https://static.wixstatic.com/media/e3a603_8f920d2a9d68484eb9592624e8e16d26~mv2.png/v1/fill/w_780,h_318,al_c,q_85,usm_0.66_1.00_0.01,enc_auto/DeePEDH_For_3DVision.png" />
</div>

> **DeePEDH SPCs enable better camera tracking and 3D reconstruction.** (a) The camera motion trajectory reconstructed from DeePEDH distance maps (green) closely tracks the ground truth (green) and provides > 10x lower RMSE than 32-bin EWH (blue). (b) 3D surface reconstruction obtained using a 32-bin EWH suffers from severe quantization artifacts. The proposed 32-bin DeePEDH method generates high quality 3D reconstructions both qualitatively and in terms of quantitative metrics. (c) semantic segmentation results for a pre-trained CEN network [42] using distance estimates from 32-bin EWH and 32-bin DeePEDH. As the distance maps from DeePEDH are significantly closer to the ground truth, the segmentation results are better than using distance images from 32-bin EWH.


# Paper

A preprint our work is currently available on arXiv. Click <a href="https://arxiv.org/abs/2408.16150" target="_blank">here</a> to access it.

# Citation

If you would like to cite us, kindly use the following BibTeX entry.

```
@misc{sadekar2024singlephoton3dimagingequidepth,
      title={Single-Photon 3D Imaging with Equi-Depth Photon Histograms}, 
      author={Kaustubh Sadekar and David Maier and Atul Ingle},
      year={2024},
      eprint={2408.16150},
      archivePrefix={arXiv},
      primaryClass={eess.IV},
      url={https://arxiv.org/abs/2408.16150}, 
}
```

# Acknowledgments

This project is supported in part by funding from the US National Science Foundation (NSF Grant # ECCS-2138471).

# Contact

Feel free to contact <a href="https://kaustubh-sadekar.github.io/" target="_blank">Kaustubh Sadekar</a> for any further discussion about our work.

