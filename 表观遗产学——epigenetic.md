表观遗传学是研究基因的核苷酸序列不发生变化的情况下，基因表达的可遗传变化的学科，包括DNA甲基化，组蛋白修饰，RNA的可变剪切，miRNA调控，转录调控，染色质可及性分析。
2024年诺贝尔生理学及医学奖授予给维克托·安布罗斯和加里·鲁夫昆在microRNA在转录后基因调控中的关键作用。
microRNA基因调控机制已存在数亿年，在人类基因组中已经超过1000个microRNA，事实表明microRNA对生物体的发育和功能具有根本性的重要作用。
这里的microRNA转录后基因调控就是表观遗传的研究范畴。
![[attachment file（image、pdf)/IMG-表观遗产学——epigenetic-2025.09.06.png|493]]
研究开放染色质的热点工具——ATAC-seq
ATAC-seq（Assay for Transposase-Accessible Chromatin with ighthroughput Sequencing）是利用Tn5转座酶探究可接近性染色质高通量测序技术
该技术通过Tn5转座酶对==特定时空==下开放的核染色质区域进行切割，获得在该时空下基因组中所有活跃转录的调控序列。因此，ATAC-seq得到的是全基因组尺度上处于开放状态的染色质区域，并且通过分析染色质开放区域的motif，可以获得潜在的活跃转录因子及其靶基因。

什么是染色质可接近性？，为什么要研究开放染色质？
DNA与组蛋白结合后形成核小体，核小体再进一步折叠压缩后最终形成染色质。DNA的复制和转录都需要将染色质紧密结构打开，从而允许调控因子结合DNA。这部分被打开的染色质，就叫开放染色质区域（Open Chromation region，OCR）。开放染色质允许调控因子结合的特性称为染色质的可接近性（Chromatin Accessibility）。

在有限的细胞核空间中，基因组大部分区域是紧密折叠的，只有需要转录的部分是开放的。一般的转录因子可以识别DNA上的motif从而结合在DNA上，而motif想要被识别，须得在开放染色质区域里。
![[attachment file（image、pdf)/IMG-表观遗产学——epigenetic-2025.09.06-1.png|462]]
![[attachment file（image、pdf)/IMG-表观遗产学——epigenetic-2025.09.06.jpg|416]]

样本要求：
细胞：2*105个

动物组织：≥50mg

植物组织：≥200mg

生物学重复：细胞系、模式生物2-3次生物学重复。人可以1次


建库测序：
测序策略：Illumina Novaseq, PE150

测序深度：40M clean reads

项目周期：45d

研究运用：
![[attachment file（image、pdf)/IMG-表观遗产学——epigenetic-2025.09.06-1.jpg|498]]
![[attachment file（image、pdf)/IMG-表观遗产学——epigenetic-2025.09.06-2.png|374]]
![[attachment file（image、pdf)/IMG-表观遗产学——epigenetic-2025.09.06-3.png|429]]
![[attachment file（image、pdf)/IMG-表观遗产学——epigenetic-2025.09.06-4.png|396]]
![[attachment file（image、pdf)/IMG-表观遗产学——epigenetic-2025.09.06-5.png|385]]
![[attachment file（image、pdf)/IMG-表观遗产学——epigenetic-2025.09.06-6.png|523]]
ATAC-seq与ChIP-seq异同点？

ATAC-Seq，是在全基因组范围内检测染色质的开放区域，可以得到蛋白质的潜在结合位点，不依赖于抗体，一般用于不知道特定的转录因子。

ChIP-Seq，明确知道感兴趣的转录因子是什么，利用特异性抗体富集蛋白质及其结合的DNA片段，从而验证蛋白质与DNA的相互作用关系。

CHIP-seq技术——染色质免疫沉淀测序
