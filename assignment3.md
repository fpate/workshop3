# Analyzing Geospatial Data and Machine Learning Methods as a Means to Understand the Intersectionality of Poverty and Gender Inequality in Nigeria
## Fatima Pate
### April 19, 2020

#### Introduction 

Home to nearly 200 million people, Nigeria is Africa’s largest economy and biggest oil producer. Unfortunately, Nigeria has and continues to face trouble in different facets of human development, one of which is poverty. Over 90 million civilians, roughly half of the population, live in extreme poverty and even more experience chronic poverty. According to the United Nations, Nigeria is growing at a rate of 3.2% a year and will have a population of 402 million by 2050 which is double its current population. Because of its current large population and the fact that it is rapidly increasing, it adds a sense of urgency to the issue of poverty. 

What makes poverty such a pressing issue is the expansive range of those it affects and what it affects. The rate of death is three times higher for those below the poverty line between the ages of 25 and 64. Similarly, poverty directly correlates to lack of education, access to health care resources, economic freedom and shorter life expectancy. The costs of it include health care costs, costs in crime, and reduced economic production. Furthermore, some of the challenges in tackling poverty are that finding accurate data and implementing data science methods can be quite hard in a large and densely populated country like Nigeria. 

Poverty in Nigeria is a gender issue. Women make up a little less than 50% of the nation’s population but according to the World Poverty Clock, they make up a bit more than 70% of those living in extreme poverty. As reported by a McKinsey report, Nigeria’s gross domestic product could grow by 23% ($229bn) by 2025 if women participated in the economy at the same level as their male counterparts. Lastly, according to UNESCO, 5.5 million girls are out of school, 40% of women have never attended school, and nearly two thirds of Northern women have no education. These statistics are so startling that it would not do the process of alleviating poverty justice to not look at gender inequality. So to make the most out of this research, poverty will be looked at through the lens of gender inequality because when women are not given equal opportunity, they are more susceptible to poverty. 

The purpose of this research is to identify how effective machine learning methods such as model-based geostatistics, Poisson regression and multinomial logistic regression are at giving data that can be used to study the intersectionality of poverty and gender inequality and to what extent one influences the other. This research question is an explanatory inquiry as it seeks to gain greater understanding of a widespread issue, poverty, through the lens of gender inequality and all that it entails. To go deeper in this matter though, sub research questions must be asked: 1. What are the roots of gender inequality in Nigeria? 2. What are the best data sets for poverty analysis? and 3. If this issue has been recognized, what is inhibiting its resolution?. To answer the firstquestion, one of the main roots of such discrimination in Nigeria is attributed to cultures and belief systems and it manifests from harmful practices such as female genital mutilation, unequal opportunities and unequal access to education and healthcare. As a consequence, this denial of basic human rights paves the way for the expansion of poverty which too often takes away the lives of many. The best data sets are the ones that include as many people as possible and are most up to date. Commonly in Nigeria, datasets are extracted from surveys and CDR data and although both have their advantages, CDR data is limited in that not everyone has a phone and surveys are hard to update in a developing country and may leave room for response bias. Lastly, globally and in Nigeria, it has been acknowledged that there is a startling number of people living in poverty and that there is a wide gender gap. But its slow resolution can be attributed to the corrupt government that mishandles money, people in power who overlook such detriment problems, and lack of accurate data. 


#### Method 1- Model-based geostatistics 

With little access to clean water and sanitation, women can not expand their freedoms such as good health, education, and employment and are thus caught up in the cycle which is poverty. In Ajisegiri, B et al. "Geo-spatial modeling of access to water and sanitation in Nigeria" was researched. Data was collected from the 2015 National Water and Sanitation Survey (NWSS) along with geo-spatial covariates(vegetation index,  aridity, land- surface temperature, brightness of nighttime lights, and estimated travel time to the nearest functioning water source) both which detail access to water, sanitation and hygiene (WASH). 

![img1](https://fpate.github.io/workshop3/Screen%20Shot%202020-04-19%20at%203.32.11%20PM.png)

The NWSS consists of household surveys which surveyed 201,842 households across 36 states, a national spatial inventory of 89,721 water points, 5,100 water schemes, and a survey on access to WASH in over 50,000 public facilities. All households and surveys points were geo-referenced to provide latitude and longitude coordinates. The method used in this researcher to map indicators of water and sanitation in Nigeria is model-based geostatistics (MBG) which applies statistical principles of modeling to geostatistical problems. Covariance between spatial locations was modeled using a Matern covariance function(determines covariance of two measurements that have different locations) where d(xi ; xj ) is the geographical separation between two points of water access, σ, v, ρ are parameters of the covariance function defining its amplitude, degree of differentiability, and scale, Kv represents the Bessel function of the second kind and Γ is the gamma function.

![img2](https://fpate.github.io/workshop3/Screen%20Shot%202020-04-19%20at%203.33.46%20PM.png)

Additionally, rather than looking at simpler non-spatial models to determine the optimum covariate selection to include in the full spatial modeling framework, the research looked at implementing "regularization" in the model which allows large covariates to be added to the main model while sacrificing a small amount of bias for a reduction in variance and reducing the amount of covariate coefficients which reduces the effects of collinearity making the model more fixed and robust. In the regularization functions below, N() is the Gaussian probability distribution function; fₓ is the Gaussian process function; y is the response; μ, C are the mean and covariance functions; and σ²I is error.

![img3](https://fpate.github.io/workshop3/Screen%20Shot%202020-04-19%20at%203.34.29%20PM.png)

To implement the above calculations, Bayesian inference was used to provide marginal posterior distributions of the proportion of individuals with access to the specified water/sanitation at each location on a 1 × 1 km spatial grid. Maps were generated in ArcGIS 10.4. 

![img4](https://fpate.github.io/workshop3/Screen%20Shot%202020-04-19%20at%203.34.59%20PM.png)

Table 1 shows the coefficients of the covariates used in the model. The  magnitude, direction and significance of the coefficients greatly varied across the indicators which allows relationships to be identified. For example, areas with more nighttime lights were associated with better sewage systems. In Table 2 below, correlation between observed and predicted values were high with 0.8 correlation for most of the indicators while sewerage connection had the lowest correlation of 0.241. The mean absolute errors were of low value indicating good model performance and the mean squared error which measures the model performance (bias and variance) was low as well. 

![img5](https://fpate.github.io/workshop3/Screen%20Shot%202020-04-19%20at%203.35.30%20PM.png)

Figure 3 below displays uncertainty levels for specific indicators. The map indicates that areas with high population density will have higher levels of estimated precision and vice versa.  

![img6](https://fpate.github.io/workshop3/Screen%20Shot%202020-04-19%20at%203.36.10%20PM.png)

In conclusion, this research gathered information from households, water points, water schemes and geospatial covariates to generate information for seven key indicators of access to WASH at a spatial resolution of 1 × 1 km. Below are two out of seven layer examples. Figure 8 is pipe water on premises and Figure 11 is open defecation. 

![img7](https://fpate.github.io/workshop3/Screen%20Shot%202020-04-19%20at%203.36.51%20PM.png)

![img8](https://fpate.github.io/workshop3/Screen%20Shot%202020-04-19%20at%203.37.15%20PM.png)

#### Method 2- Poisson Regression and Multinomial Logistic Regression Model 

In Bola Lukman Solanke's "Marriage Age, Fertility Behavior, and Women’s Empowerment in Nigeria", the relationship between age at first marriage and women’s fertility behavior and empowerment was analyzed. Liberal feminist theory which aims to empower women and improve their access to  public institutions while bringing women’s issues to the forefront of national discussion (Walter, 1998), is the foundation of this research. Data were extracted from the 2013 Nigeria Demographic and Health Survey (NDHS) which provides demographic and health indices information such as fertility, marriage, family planning, adult and childhood mortality, domestic violence, and HIV/AIDS. The Poisson regression which indicates which X-value works on a Y-value, was used to examine the relationship between age at first marriage and children ever born. Multinomial logistic regression which applies "to the analysis of discrete dependent variables when the dependent variable has more than two nominal or unordered categories" (Solanke, B. L.), was used to examine the relationship between age at first marriage and empowerment.

In this study, the results of the poisson regression model are represented as the incident rate ratios (irr) which estimate the incidence of children ever born in a given category. Three poisson regression models were created: 1. model for only age at first marriage 2. model for the socio-economic factors and 3. model for mediating factors. Three other models for multinomial logistic models were created: 1. age at first marriage 2. mediating factors 3. socio-economic factors. In Table 2 below, patterns of marriage, fertility and empowerment across 6 political zones are shown. More than a quarter of women married at the age 14 years or younger but the most common interval was from ages 15-19 in the north-western region. Similarly, the number of marriages at the age of 25 or older was higher in the southern regions. Table 2 also displays contraceptive use. Only 15.7% of women were using at least one method of contraception, with higher use in the south. Pregnancy termination was also higher in the south. Overall, there are higher levels of women empowerment in the south than in the north. 

![img9](https://fpate.github.io/workshop3/Screen%20Shot%202020-04-19%20at%203.38.00%20PM.png)

Table 3 presents the results of the Poisson regression model. All three models indicate that age at first marriage is related to children ever born. In Model 1, the incidence rate of children born for women ages 14 or younger is higher than the incidence rate of children born for women aged 15-19. Model 2 indicates that incidence of children born decreases as the age of first marriage increases. Lastly, in Model 3, incidence of children born was higher for women who had no access to mass media and lower for women who had low to moderate access to mass media.

![img10](https://fpate.github.io/workshop3/Screen%20Shot%202020-04-19%20at%203.38.25%20PM.png)

Table 4 presents the results of the multinomial logistic regression model. Across all three models, age at first marriage has a significant relationship to empowerment. For example in Model 1, the relative risk of being in the high empowerment category instead of moderate category increases by a factor of 2.0988 for those 15 to 19 years of age at first marriage compared to those married at 14 years or less. However, in the low empowerment category,  the relationship between age at first marriage and empowerment was not sta- tistically significant. 

![img11](https://fpate.github.io/workshop3/Screen%20Shot%202020-04-19%20at%203.38.39%20PM.png)

#### Discussion

Although Ajisegiri, B et al. and Solanke, B. L focused their research on different aspects of development in Nigeria and used varying machine learning models, in the context of my research, both must be analyzed through the lens of the other. Ajisegiri, B et al. used model-based geostatistics to map out areas of water and sanitation. Solanke, B. L used two models, Poisson regression and multinomial logistic regression, to determine the relationship between age at first marriage, fertility and women empowerment. The relationship of these two articles appears when studying the extent of intersectionality between poverty and gender inequality. Lack of clean water and sanitation decreases any human beings freedoms as described by Amartya Sen’s Development As Freedom (1999). Specifically, it decreases women's freedoms because clean water and sanitation is necessary for menstrual hygiene, pregnancy, and overall general health. By getting a greater understanding of the extent of gender inequality through articles like Solanke, B. L and with high-resolution maps that indicate low quality of water which indicates high rates of poverty, better solutions for poverty and gender inequality can be generated. All three models, MBG, poisson regression and multinomial logistic regression contribute to the research in different ways. MBG allows for better mapping of populations, Poisson regression tells which explanatory variables influence the response variable and multinomial logistic regression allows for more than two groups of the outcome variables for probability analysis.  To begin to answer the question of “How effective are machine learning methods such as MBG, Poisson regression, and multinomial logistic regression at giving data that can be used to study the intersectionality of poverty and gender inequality and to what extent does one influence the other?”, these methods are most effective when combined with one another and by the results of both articles, poverty and gender inequality greatly influence one another. 



#### References

[1] Ajisegiri, B., Andres, L. A., Bhatt, S., Dasgupta, B., Echenique, J. A., Gething, P. W., … Joseph, G. (2019). Geo-spatial modeling of access to water and sanitation in Nigeria. Journal of Water, Sanitation and Hygiene for Development, 9(2), 258–280. doi: 10.2166/washdev.2019.089

[2] Solanke, B. L. (2015). Marriage Age, Fertility Behavior, and Women’s Empowerment in Nigeria. SAGE Open, 5(4), 215824401561798. doi: 10.1177/2158244015617989

[3] Gill, R. (2000). Feminist Review, (64), 139-143. Retrieved April 19, 2020, from www.jstor.org/stable/1395714

