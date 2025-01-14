The focus on enantiopure drugs has forced the pharmaceutical industry to look for cost efficient methods of production. These methods are required to be efficient enough to separate the enantiomeric target from a racemic mixture. One way that this has been achieved is through the direct crystallisation in a racemic mixture. This stochastic process is poorly understood and leads to long and costly experiments. To improve upon this randomness, mathematical models can be developed to predict the thermodynamic values from the separation process. These models look to reduce the experimental time necessary for solubility diagrams. This project was made in collaboration with Imperial College London's [Institute of Molecular Science and Engineering](https://www.imperial.ac.uk/molecular-science-engineering/) and [BASF](https://www.basf.com). The goal was to develop a software to model solubility diagrams of enantiomers.

Asymmetrical crystallisation of a chemical molecule can be traced back to experiments performed by Arago and Biot in 1811. This experiment showed different rotations of polarised light on cut crystals. This was later reinforced on organic products, where similar results were shown [^1] . The study of stereochemistry is formally attributed to Louis Pasteur, who in 1848 detected different crystal structures after the crystallising the racemic sodium ammonium salt of tartaric acid. Like Arago and Biot, he also saw that light rotated differently on these crystals [^2] . The key discovery was presented by Van 't Hoff and Le Bel during independent research experiments. What awarded Henry Van’t Hoff the first ever Nobel prize in Chemistry was detailing the relationship between three-dimensional molecular structure and optical activity and the concept of the asymmetric carbon atom [^3] [^4] .

[Stereoisomers](https://en.wikipedia.org/wiki/Stereoisomerism) are molecules that have both the same molecular formula and connectivity but differ in their three-dimensional arrangement. Stereoisomers can be either diastereomers or enantiomers. Diastereomers have different arrangement of atoms that cannot be optically rearranged to form the counterpart. Enantiomers are mirrored non-superposable molecules that could be rearranged via a chiral shift to form the opposite. The standard nomenclature is the R/S system, used to identify distinct enantiomers. 

![Enantiomers](assets/enantiomers_1.png)

Enantiomeric molecules will share the same chemical and physical properties in solution which make them indistinguishable components. In biological systems the function of a protein is determined by its shape, and the shape of a protein can be defined by its amino acid components. 19 out of the 20 amino acids that naturally occur in nature are enantiomers, and only the S enantiomers are used for protein synthesis [^5] . This exclusivity extends to pharmaceuticals. Omeprazole (also known as Prilosec) has been used for years as a medication for gastrointestinal diseases. This drug is the crystal product of both enantiomers of omeprazole, commonly known as the racemate. In the treatment of gastrointestinal symptoms, only the S-enantiomer will have any medicinal properties. The R-enantiomer won’t have the effect of its mirror molecule until it has produced a chiral shift in vivo. The more challenging example is that of salbutamol (also known as albuterol) which is an enantiomeric drug that is used to treat asthma and asthma attacks. R-salbutamol causes the opening of airways in the lungs, but its mirror enantiomer produces a variety of unpleasant side-effects. This apparent limitation has pushed the industry to develop enantiopure drugs, or enantiomeric drugs of only one enantiomer. In the case of omeprazole, even though its pharmacological benefits are still debated, there is no doubt that it has been a financial success [^6] [^7] .

![Ketamine](assets/enantiomers_2.png)

The symmetrical properties of enantiomers in solution makes the separation of these components a challenge. To synthesize enantiopure medications, the product needs to be purely composed of our desired enantiomer crystal. In very few cases the process is very simple and chiral pooling, or a chiral catalyst can be used [^8] . The most common procedure to separate enantiomeric molecules is to use the racemic method. In which you use chiral mobile phase additives to resolve a racemate into a pure enantiomer or you utilise a chiral derivatizing agent for enantioseparation. Either process is costly and time-consuming but have been consistently used in the pharmacological industry [^9]. These methods have been successful in both small processes and in batch processes but haven’t been thoroughly researched in continuous processes. There are some obvious economic benefits to transitioning to continuous processes. This lucrative opportunity interests pharmaceutical companies that want to maximise their production while keeping costs low. Therefore, one method that can be considered is the direct crystallisation of one enantiomer in a racemic mixture [^10] . This process achieves enantiospecific crystallization by modulating the concentration of the solutes. By saturating the solution of a mixture with one of the solutes, only the seeded component will crystallize, leaving only the opposite enantiomer in the solution. In a mixture of enantiomers, crystallization can occur in two ways. In conglomerates, crystallization occurs independently while racemic compounds produce a racemate crystal at certain compositions. 90% of enantiomeric mixtures will crystallise as racemic compounds and produce a racemate, which means solubilities are complex to determine [^11] .

![Preferential Crystallisation](assets/PreferentialCrystallisation.png)

Knowledge of the points of solubility, as a function of their temperature and composition, is essential to produce enantiopure products from a racemic compound. These experiments require extensive trial-and-error results that are both costly and time-consuming. The process is also solvent-solute specific, so the process needs to be repeated across any combination of components. To circumvent this requirement, we can develop a thermodynamic model in order to predict the possible solubility values. 

Solubility of a binary system can be predicted using the equations put forth by Schröder and van Laar [^12]. A pure solid can be heated until melting temperature has been achieved during constant pressure. At melting temperature the solid will enter the solid-liquid transition phase. The species can then be cooled carefully as a metastable fluid down to its original temperature.

```math
ln(\frac{f^S(Tm, P)}{f^S(T, P)}) = - \int_{T}^{T_m} (\frac{H^S-H^{ig}}{RT^2})dT 
```

```math
f^S(T_m, P) = f^L (T_m, P) 
```

```math
ln(\frac{f^L(T, P)}{f^L(T_m, P)}) = - \int_{T}^{T_m} (\frac{H^L-H^{ig}}{RT^2})dT
```

```math
ln(\frac{f^L(T, P)}{f^S(T, P)}) = -\int_{T}^{T_m} \frac{\Delta H_{melt}(T_m)+(T-T_m)\Delta C_p}{RT^2}dT
```

```math
\Delta H_{melt} = H^L(T_m) - H^S(T_m)
```

```math
H^L = H^L(T_m) + C_p^L(T-T_m)
```

```math
ln(\frac{f^L(T, P)}{f^S(T, P)}) = \frac{\Delta H_{melt}}{R}(\frac{1}{T}-\frac{1}{T_m}) - \frac{T_m}{R}\Delta C_p (\frac{1}{T}-\frac{1}{T_m} - \frac{\Delta C_p}{R} ln (\frac {T}{T_m})
```

Under the assumption that the chemical potential of any species in all phases can be assumed to be identical. This requires the assumption that the fugacity of a dissolved solute equals the fugacity of the undissolved species in the solid state. During ideal interactions, the mutual solubility of the liquid and solid phase is ignored. 

```math
ln(x^{sat}_i \space \gamma^L_i) = \frac{\Delta H_{melt}}{R}(\frac{1}{T}-\frac{1}{T_m}) - \frac{T_m}{R}\Delta C_p (\frac{1}{T}-\frac{1}{T_m} - \frac{\Delta C_p}{R} ln (\frac {T}{T_m})
```

```math
f^S_i = f^L_i (T, P, x_i)
```

```math
f^S_i = x^{sat}_i \space \gamma^L_i \space f^L_i (T, P)
```

The heat capacity below the melting point cannot be experimentally calculated. Its shape is not clearly defined either, which means the value cannot be extrapolated [^13]. Approximations between the solid and liquid heat capacities have been developed, such as making the value equal at the temperature of fusion under the assumption of being temperature insensitive [^14]. In most cases, good results can be produced when neglecting the heat capacity contribution which leads to the simplified binary solubility equation. The ideal solubility of a compound (``x_i^{sat}``) in a solution can be calculated by knowing the compound’s calorimetric properties (``Δ_{fus}H_i, T_m``) and the activity coefficient (``\gamma_i^L``). The calorimetric properties of a solute can be easily determined and used irregardless of the solvent.

```math
ln(x^{sat}_iγ^L_i) = \dfrac{Δ_{fus}H_i}{R}(\dfrac{1}{T_{m,i}} - \dfrac{1}{T})
```

The activity coefficient of a non-ideal mixture must be computed using thermodynamic models. Traditionally, empirical methods have been used to determine the activity coefficient. Empirical models such as Wilson, NRTL (Non-random two liquid), UNIQUAC (Universal Quasichemical), etc., have been successfully used in industry to model pharmaceutical solubility [^15] . These equations are dependent on interaction parameters derived from experimental research. Once obtained, the unique solute-solvent parameters can be used in any composition at a broad temperature range. Completely predictive models have also been used to determine the activity coefficient with limited success. The required information can be determined by either quantum calculations using COSMO-RS (Conductor like Screening Model for Real Solvents) or equations of state such as PC-SAFT (Perturbation-Chain Statistical Associating Fluid Theory). Both methods will yield an acceptable activity coefficient, but their use is considered less reliable compared to empirical models if the experimental data is available [^16] . Recently, modifications to the empirical methods have yielded semi-empirical formulations that attempt to minimize error. Predominantly, this comes as the SAC modification (Segment Activity Coefficient), where the molecule’s surface interactions are divided in segments and each type of solute-solvent interaction (hydrophobic, hydrophilic, and polar) has been predefined.

The solubility data of enantiomeric mixtures is easily interpreted using a ternary phase diagram. In this three-variable chart, every point represents a composition of the R/S enantiomer and the solvent of the solution. The Schröder and van Laar equation allows for the solubility lines of the enantiomers to be calculated. This is the case for conglomerates, but in most situations the mixture will behave as a racemic compound, where the racemate must be accounted for. Like single enantiomers, we require the activity coefficient of the racemate to model solubility. An expansion of the Schröder and van Laar equation leads to a modified Prigogine and Defay equation [^17] [^18] . This relationship can be used to determine the solubility point of the racemate with the activity coefficient of the constituent enantiomers. This allows for the calculation of the racemate solubility curve and determining the eutectic points of the solution. Knowing the eutectic points gives us enough information to design a process where we can produce one kind of crystal enantiomer.

![Ternary Phase Diagram](assets/tpd.png)

```math
ln \space [4 \space x_i^{sat}\gamma^L_ix_j^{sat}\gamma^L_j] = \dfrac{Δ_{fus}H_{rac}}{R}(\dfrac{1}{T_{m, rac}} - \dfrac{1}{T})
```

[^1]: Leclercq F. Arago, Biot, and Fresnel Elucidate Circular Polarization. Revue dhistoire des sciences. 2013;66(2):395-416.

[^2]: Pasteur L. Memoires sur la relation qui peut exister entre la forme crystalline et al composition chimique, et sur la cause de la polarization rotatoire. Compt. rend.. 1848;26:535-8.

[^3]: Hoff JH. Voorstel tot uitbreiding der tegenwoordig in de scheikunde gebruikte structuur-formules in de ruimte: benevens een daarmee samenhangende opmerking omtrent het verband tusschen optisch actief vermogen en chemische constitutie van organische verbindingen. Greven; 1874.

[^4]: Le Bel JA. On the relations which exist between the atomic formulas of organic compounds and the rotatory power of their solutions. Bull. Soc. Chim. 1874;22:337-47.

[^5]: Bertrand M, Chabin A, Brack A, Westall F. Separation of amino acid enantiomers VIA chiral derivatization and non-chiral gas chromatography. Journal of Chromatography A. 2008 Feb 8;1180(1-2):131-7.

[^6]: Asghar W, Pittman E, Jamali F. Comparative efficacy of esomeprazole and omeprazole: Race-
mate to single enantiomer switch. DARU Journal of Pharmaceutical Sciences. 2015 Nov;23(1):50.
Available from: https://doi.org/10.1186/s40199-015-0133-6.

[^7]: Conley JG, Bican PM, Ernst H. Value Articulation: A Framework for the Strategic Management of
Intellectual Property. California Management Review. 2013;55(4):102-20.

[^8]: Hawkins JM, Watson TJN. Asymmetric Catalysis in the Pharmaceutical Indus-
try. Angewandte Chemie International Edition. 2004;43(25):3224-8. Available from:
https://onlinelibrary.wiley.com/doi/abs/10.1002/anie.200330072.

[^9]: Mane S. Racemic drug resolution: a comprehensive guide. Anal Methods. 2016;8:7567-86. Avail-
able from: http://dx.doi.org/10.1039/C6AY02015A.

[^10]: Lorenz H, Sheehan P, Seidel-Morgenstern A. Coupling of simulated moving bed chromatogra-
phy and fractional crystallisation for efficient enantioseparation. Journal of Chromatography A.
2001;908(1):201-14. 13th International Symposium on Preparative and Process Chromatography.
Available from: https://www.sciencedirect.com/science/article/pii/S0021967300009924

[^11]: Gänsch J, Huskova N, Kerst K, Temmel E, Lorenz H, Mangold M, et al. Con-
tinuous enantioselective crystallization of chiral compounds in coupled flu-
idized beds. Chemical Engineering Journal. 2021;422:129627. Available from:
https://www.sciencedirect.com/science/article/pii/S1385894721012146.

[^12]: Jacques J, Collet A, Wilen SH. Enantiomers, racemates, and resolutions. AGRIS. 1981:369-71.

[^13]: Neau SH, Flynn GL. Solid and liquid heat capacities of n-alkyl para-aminobenzoates near the
melting point. Pharmaceutical research. 1990;7(11):1157-62.

[^14]: Nti-Gyabaah J, Chmielowski R, Chan V, Chiew Y. Solubility of lovastatin in a family of six alco-
hols: Ethanol, 1-propanol, 1-butanol, 1-pentanol, 1-hexanol, and 1-octanol. International journal of
pharmaceutics. 2008;359(1-2):111-7.

[^15]: Salimi M, Zarenezhad B, Fakhraian H, Choobdari E. Thermodynamic modeling of chiral com-
pounds solubility using Correlative and predictive models. Journal of Applied Solution Chemistry
and Modeling. 2015;4(3):143.

[^16]: Tung HH, Tabora J, Variankaval N, Bakken D, Chen CC. Prediction of Pharmaceutical Solubil-
ity Via NRTL-SAC and COSMO-SAC. Journal of Pharmaceutical Sciences. 2008;97(5):1813-20.
Available from: https://www.sciencedirect.com/science/article/pii/S0022354916325564.

[^17]: Prigogine I, Defay R. Chemical thermodynamics. 1958.

[^18]: Tulashie SK, Kaemmerer H, Lorenz H, Seidel-Morgenstern A. Solid−Liquid Equilibria of Mandelic
Acid Enantiomers in Two Chiral Solvents: Experimental Determination and Model Correlation. Jour-
nal of Chemical & Engineering Data. 2010;55(1):333-40.
