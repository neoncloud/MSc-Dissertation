# 原计划书

People with face acne problem may have concerns about how they look. When deciding on a skin care product, they may want to know how their acne problem can be improved after they use those products. However, there exists no such techniques for simulating the changes of acne on facial skin of different skin tones. In this project, we propose to explore advanced computer vision or deep learning techniques to build a novel system which can simulate skin acne changes.

## Description of the Project:
In this project, the student should explore possible approaches to build a system for the skin acne simulation. This system should first the segment facial acne. On each segmented acne, and the simulation operation is conducted. Therefore, the student need to learn to apply image segmentation method to segment the acne. Then, the student may explore image processing or deep learning methods to implement the simulation operations. Moreover, as people have different skin tones, from fair to dark, the variety of skin tones may affect the segmentation and simulation models. Hence, the student need to explore generalization methods to improve the segmentation and simulation methods’ performance against the diversity of skin tones.

To achieve the above objectives, the student needs to conduct literature study about image segmentation, image warping, image translation, and so on. Then, the student needs to do programming to implement and improve the simulation and segmentation methods, and conduct experiments for analysis.

What you will learn & do:
1. Algorithm implementation: the student needs to implement some image/video processing and computer vision techniques, such as acne detection, image warpping, etc.
2. Data understanding: the student needs to understand the face image data to design acne simulation operations
3. The required knowledge and skill for this project can be summarized as follows: (a) MatLab; (b) Python & Pytorch; (c) OpenCV; (d) deep learning and computer vision

# 主题
## 现状
色斑的生理学特征，成因和主要性状（简略）：由于其复杂的机理，导致定义和建模的困难；现有的算法难以准确而自然地编辑色斑的外观。（提出问题和 gap）

## 提出的方法
皮肤光学性质模型，次表面散射原理；借用图形学中一些近似算法，对色斑的外观进行建模，实现色斑和基底皮肤的分离，从而进行有真实感的修改

一个新颖的，能较好估计皮肤色素的相对浓度的框架被提出。通过这个框架，色斑和皮肤能较好地分离。又提出一个参数化的色斑模型，实现色斑的空间的分布的稳健拟合。

## 工程实现
我们使用 python + opencv 编写了一个处理后端，能自动分析和拟合 ROI 中色斑的浓度

* 文献回顾
  * 皮肤色素和色斑
  * 皮肤模型和渲染
  * 可控的面部编辑方法
* 方法
  * 分层的皮肤模型和处理
    * 纹理层
    * 色素层：次表面散射的近似
  * 色彩空间分解
  * 色斑建模和拟合方法
* 实验
  * 数据集
  * 参数搜索
  * 工程实现 和 demo
* 结果和分析
  * 客观评价
    * 真实性
    * 可控性
    * 多样性
    * 跑分
  * 主观评价
    * 调查问卷
    * 结果
* 总结

# Chap2
## Skin Chromophores & Pigmentation
1.  M. Doi and S. Tominaga, ‘Spectral estimation of human skin color using the Kubelka-Munk theory’, presented at the Electronic Imaging 2003, R. Eschbach and G. G. Marcu, Eds., Santa Clara, CA, Jan. 2003, p. 221. doi: 10.1117/12.472026.

The main pigments inside the skin are melanin and hemoglobin. The melanin makes the skin color darker. The hemoglobin is included in blood. The red color of blood is due to the hemoglobin. The hemoglobin is distinguished into oxy-hemoglobin and deoxy-hemoglobin, which have different absorption characteristics each other. Moreover, the skin includes two other pigments of carotene and bilirubin. These pigments make the skin color yellowish. Figure 2 shows the absorption of these five pigments [5]. It is suggested in [5] that carotene has almost the same absorption as the one of bilirubin. The spectral reflectances of human skin change among different parts of body and also among individuals. The change of mental conditions also can influence the spectral reflectance of skin. We assume that these changes are caused by two factors, the amount of each pigment and the thickness of skin. In order to determine a relation between skin spectral reflectance and these factors, we assume a simple optics model of skin as shown in Figure 3. The skin optics model has two layers including pigments. These layers are called epidermis and dermis. The epidermis is the outer layer of the skin that includes the pigments of melanin and carotene. The dermis is located under the epidermis. This layer includes the pigments of oxy-hemoglobin, deoxy-hemoglobin and bilirubin. It should be noted that the optical properties in each layer tissue, such as scattering, refracting, and absorption depend on wavelength. We assume that under the dermis there is hypodermis consisting of white fat. So the reflectance of the hypodermis is set to 1. In this model, a part of incident light is reflected between the skin surface and the air. The remaining light penetrating the surface is absorbed and scattered in the layers. The light ray that reaches the hypodermis layer is reflected at interface between the two layers and return into the upper layer.

2. R. R. Anderson and J. A. Parrish, ‘The Optics of Human Skin’, Journal of Investigative Dermatology, vol. 77, no. 1, pp. 13–19, Jul. 1981, doi: 10.1111/1523-1747.ep12479191.

Fortunately, many of the major chromophores are normally confined to a single layer. Melanin is confined to the epidermis and stratum corneum, whereas the various forms of hemoglobin are confined to vessels of t he dermis, and only indirectly exert a ny influence on optical radiation densities within the overlying epidermis. Considering the absorption spectra and localization of the major cutaneous pigments, and optical scattering for each layer, it is in theory possible to arrive at mathem atical descriptions of cutaneous optics which include m any of the major variables in vivo, and which can be used to analyze the skin a nd its photobiologic responses a nd to approximate actual Qptics of human skin. skin is always between 4% and 7% over the entire spectrum from 250-3000 nm, for both white and black skin [14,15]. This same a ir-tissue optical interface also causes internal reflection of diffuse, back-scattered radiation, which is an important consideration when analyzing remittance spectra of skin: Because the surface of the stratum corneum is not smooth and planar:

Melanin is a r emarkably s table protein-polymer complex, the crnomophoric backbone of which survives attack by proteases, acids and bases. Caucasian melanosomes typically contain a greater number of melanin granules, but less total melanin, than Negroid or Mongolian melanosomes, and also appear to suffer greater degradation within kera tinocytes. The optical effects associated with dispersed "melanin dust" in Caucasians versus intact m elanosomes have not been quantitated, but it is likely that, unless the crnomophoric backbone is degraded, dispersal of melanin pigment• in Caucasian stratum corneum affords somewhat greater protection than would the same quantity of melanin sequestered in intact melanosomes. An interracial study of epidermal transmittance by Kaidbey, et al [36] suggests that the large racial differences in sensitivity to UV of 10-to 30-fold [37,38] correlate poorly with the small racial differences of approximately 3-fold noted in stratum corneum transmission. However, the minimal erythema dose of black and white subjects has never been directly compared with accurate stratum corne um or epidermal transmitta nce m easurements of samples from t he sam e subjects, split at various levels in the tissue. Urocanic acid is thought to play some role as a n "endogenous sunscreen" of the epidermis and stratum corneum [39,40). Recent observations [41] show that extraction of water soluble, diffusible, UV -absorbing compounds from skin into topically applied water accounts for the up to 50% increased sensitivity of skin to UVB radiation after hydrating the skin for prolonged periods. While most of the material extracted is lipid or protein, a small fraction (about 0.2%) of the material is urocanic acid . Because of its high extinction coeffi cient (18,800 1M-I cm-I at 277 nm, pH 7.4), however, urocanic acid accounted for approximately 75% of the optical absorbance of the extracted materials. Because extensive exposure to sunlight is often associated with sweating, which deposits urocanic acid on the skin surface [39], it is possible that sweating may serve to some extent as a t hermally-induced photoprotective mechanism.

The stratum corneum a nd e pidermis provide a n optical barrier primarily by a bsorption of radiation, a nd to a lesser d egree, by optical scattering. In the ultraviolet region less than 300 nm, aromatic amino acids, nucleic acids, urocanic acid, a nd mela nin can be d efin ed as major epidermal abso rbe rs. Hyperplasia, m elanogenesis, and perhaps uroca nic acid synthesis, form an inducible photoprotective system . Th e relative importa nce of these varia ble proteetive fa ctors is wa velength-dependent a nd varies between skin sites a nd individuals. In the wavelength region 350-1200 nm, m elanin is the major absorber of radiation in the epidermis, especia ll y at shorter wavelength s. One can manipulate t h e optics of the epidermis by val"ious stimuli including UV radiation, by extraction in vivo of UV -absorbing compounds, most notably urocanic acid, a nd in t he case of psoriasis by a s uperficial refi'active index matching mechanism when oil is a pplied. A rigorous model, with data, for epid ermal optics is lacking. The d ermis may be considered a t urbid tissue matrix wi th which optical scattering is an inverse fun ction of wavelength a nd largely defin es the d epth' of optical penetration. Absorption bands of blood-borne cillomophores, especially bilirubin a nd oxyhemoglobin, are apparent in remittance spectra of skin, a nd such spectra can be used to monitor or a nalyze serum bilu'ubin, vasc ular , or pigmentation responses. D espite many complicating factors, it is possible to a pproximate t he optics of the dennis using radiation-tra nsfer t heori es, and a simple model is presented.


3. C. Donner and H. W. Jensen, ‘A Spectral BSSRDF for Shading Human Skin’.

The most striking feature of skin is its color, which is determined by absorbing chromophores distributed in the different layers. The most prominent chromophores that affect skin appearance are hemoglobin and melanin [AP81]. Hemoglobin is responsible for carrying oxygen throughout the body, and is the primary constituent of red blood cells. It comes in both oxygenated and deoxygenated forms, each with a slightly different properties. The absorption spectra of both oxy- and deoxy- hemoglobin are shown in Figure 1. Note the characteristic peaks in oxy-hemoglobin at 542nm and 547nm. The other chromophore, melanin, is not actually a pure substance, but is composed of different polymers, and varies in color from light yellow to very dark brown or black [AAB∗02]. Lighter melanin is composed mostly of pheomelanin, while the darker type is generally eumelanin. Different concentrations of these basic molecular building blocks are believed to produce the various pigmentations of skin and hair seen in the natural world. Both melanins have a characteristicly broad and smooth absorption band, with highest absorption in the UV range, decaying as wavelength increases (see Figure 1). This property likely makes them good safeguards against solar radiation. Recent work suggests that the the type, rather than total concentration, of melanin is the primary factor in skin coloring [AAB∗02]. Although the most significant absorber in the darkest skin is eumelanin, in somewhat lighter skin colors (e.g. Asian skin), there is a wide range of concentrations of the different types of melanin [AHC∗01, AAB∗02, IW06, WKK∗06]. The particular type distribution varies by individual, even within a single ethnic group. There are small concentrations of other chromophores carried in the blood, such as bilirubin and beta-carotene, but their visible contribution in healthy skin is negligible [AP81, MM02]. The other structures in skin, such as internal cellular structures and organelles, also play some small part in absorbing light.

什么让我们的皮肤呈现多样的色彩？当光线透射进皮肤，不同波长的能量被发色基团选择性地吸收，经过皮肤组织的散射后被我们观察到，并呈现出独有的色彩。

What gives our skin its diverse colors? When light is transmitted into the skin, energy of different wavelengths is selectively absorbed by the chromophores, scattered by the skin tissues and then observed by us and rendered in unique colors. The color of human skin and skin pigmentations is primarily influenced by several key chromophores, namely melanin, hemoglobin, carotene, and bilirubin. These pigments, each with unique optical properties, contribute to the skin's overall coloration and appearance.

Melanin: This is the primary determinant of skin color, providing shades from light to dark. Melanin absorbs across a broad range of the visible spectrum but particularly in the ultraviolet (UV) region. This absorption is crucial as it protects the skin from UV radiation damage. The concentration and distribution of melanin can vary widely among individuals, leading to a diversity of skin tones.

Hemoglobin: Found in red blood cells, hemoglobin gives blood its red color. The optical properties of hemoglobin vary between its two forms: oxy-hemoglobin (oxygen-rich) and deoxy-hemoglobin (oxygen-poor). These forms have distinct absorption peaks in the visible spectrum, contributing to the reddish undertones of skin.

Carotene and Bilirubin: These pigments impart a yellowish hue to the skin. They absorb light in the blue region of the spectrum, which complements the reds of hemoglobin and the browns of melanin, contributing to the overall skin tone.

The formation of skin pigmentations, such as brown spots or red spots, is often associated with an overproduction or uneven distribution of skin chromophores. These pigmentations can result from various factors, including genetic predisposition, hormonal changes, sun exposure, and aging. In response to UV radiation, melanocytes (melanin-producing cells) increase their production of melanin as a protective mechanism, which can lead to localized darkening of the skin.

图 x 中我们展示了典型的几种皮肤色素的光谱吸收系数。两种血红素都在从400nm 到 450nm 以及 520nm 到 600nm 有较高的吸收系数，这使得皮肤呈现粉红色的外观。而黑色素对UV和蓝紫色有较为强烈的吸收，使得皮肤呈现棕色到黑色的外观。