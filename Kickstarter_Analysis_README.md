
					Kickstarter Campaign 
###Project Overview
	The purpose of this analysis is to examine the outcomes for Kickstarter projects based on launch dates and funding goals and to provide insights on the success or failure of potential projects based on these factors for our client Louise and her play Fever.  

###Background
	The dataset provided for this analysis spans 8 years (2010-2017) and includes 4225 projects across 9 categories and 41 sub categories. The Kickstarter campaign currently being launched is the play Fever, and so the analysis focuses on the theatre category and play sub category. 

###Analysis 
	The analysis was performed in two phases, based on launch dates and funding goals respectively. 

	##Phase 1: Launch Dates
		When reviewing the dataset to determine the best time to launch a Kickstarter campaign, we analyzed the time of year that campaigns were historically launched and compared their success and failure rates, focusing on the Theatre category. The data was grouped by outcomes, identifying successful, failed and cancelled projects. 

	##Results:
 		As noted in the graph "outcomes based on launch date (https://github.com/Roland791/kickstarter-analysis-repository/blob/main/Resources/Theater_Outcomes_vs_Launch.png), the results indicate that while May June and July had the highest total project launches they also had the highest number of successes. The months with the lowest chance of success are November and December, indicating that the end of the year, and the Holiday season may play a role in how much support a project will see.

	##Challenge:
		The biggest challenge when building out this dataset revolved around the dates associated with each project. Since the date is provided using the antiquated Unix timestamp it requires conversion using a special formula (https://stackoverflow.com/questions/46130132/converting-unix-time-into-date-time-via-excel)

	##Phase 2: Funding Goals
		The dataset for funding goals was analyzed by investigating the initial request amount for projects and comparing the success or failure within predetermined ranges. Using the number of results against each outcome and dividing by the total projects for that range, we were able to calculate a percentage success and failure rate for comparison.

	##Results:
 		(https://github.com/Roland791/kickstarter-analysis-repository/blob/main/Resources/Outcomes_vs_Goals_plays.png)
		Generally speaking, the smaller the requested amount, the higher the probability of success. There are two exceptions to that, with the 35,000 range and the 40,000 range both showing a 67% success rate, however, with only 6 and 3 projects in each range respectively, these numbers are outliers within the dataset and are unfortunately less reliable.    

	##Challenge:
		The most complicated portion of this analysis was in building out the formulas for each of the cost ranges. There were actually three different formula setups that needed to be used, depending on the range. All of the formulas limit the count for the results by focusing only on the “plays” category and then the related column outcome (“successful” in the sample below) :
			=COUNTIFS(Kickstarter!$R:$R,"plays",Kickstarter!$F:$F,"successful")
		However, an additional set of modifiers need to be added for the range. For the “less than 1000” range, the formula was relatively simple, requiring only a simple “Less than 1000”
			=COUNTIFS(Kickstarter!$R:$R,"plays",Kickstarter!$F:$F,"successful",Kickstarter!$D:$D,"<1000")
		The majority of the other ranges (excluding the 50,000 and above range) require two amount modifies, one for the minimum amount of the range and one for the maximum:
			=COUNTIFS(Kickstarter!$R:$R,"plays",Kickstarter!$F:$F,"successful",Kickstarter!$D:$D,">=1000",Kickstarter!$D:$D,"<=4999")
		This final range set as written requests that the field include amounts “greater than 50,000”, however this request isn’t inclusive of the 50,000 amount itself and would miss several datapoints, so we modified the range to read “50,000 or above”:
			=COUNTIFS(Kickstarter!$R:$R,"plays",Kickstarter!$F:$F,"successful",Kickstarter!$D:$D,">=50000")

###Conclusions

	##What are two conclusions you can draw about the Theater Outcomes by Launch Date?
		The results indicate that while May June and July had the highest total project launches they also had the highest number of successes. The months with the lowest chance of success are November and December, indicating that the end of the year, and the Holiday season may play a role in how much support a project will see.

	##What can you conclude about the Outcomes based on Goals?
		Generally speaking, the smaller the requested amount, the higher the probability of success. There are two exceptions to that, with the 35,000 range and the 40,000 range both showing a 67% success rate, however, with only 6 and 3 projects in each range respectively, these numbers are outliers within the dataset and are unfortunately less reliable.

	##What are some limitations of this dataset?
		The first major limitation noted during the project analysis is the small number of data points in some areas (such as the outcomes based on goal ranges), which yielded a sampling that isn’t large enough to reliably draw conclusions from compared to the other data points. Having a greater number of projects in those ranges would help with consistency. 
		Secondly, additional data categories could be included that would expand the understanding of how pledges are being made, such as the different backer tiers for each project and the number of pledges per tier.  

	##What are some other possible tables and/or graphs that we could create?
		There are several different other ways the information could be analyzed, including looking at the length of time a project is active, the impact of spotlight and staff picks on outcomes, and comparing the average backer amounts to the goals and dates. 
