# Credit Derivative Pricing Model


We propose default correlation model and four credit default derivative pricing models, namely, single name credit default swaps with counterparty risk, First-to-Default basket default swaps, FirstNofN basket default swaps, and FirstLoss trades. 

The purpose of the default correlation model is to predict the probabilities of single- and multiple- default events for a collateral asset pool, which are then converted into pricing for various credit derivatives. The model is built upon the hazard rate curves with certain assumptions on default correlation among the obligors in the collateral pool. The hazard rate curve, which represents the unconditional default probability of an obligor, is calibrated by the market information of single name credit default swap and has been re-reviewed in phase one.

Assume a set of obligors, , in which each obligor is described by a hazard rate curve  , a recovery rate , and associated with a default time  .  The survival probability of obligor   is then expressed as:

(1) 		 ,

and the default probability is  .

In general the model is within the framework of the multivariate Poisson distribution, in which the default correlation between obligors is introduced solely as a relationship between their hazard rate curves.  We have default correlation between names   and  defined as
(2)		 ,		
where   is the Poisson arrival intensity for joint defaults or joint hazard rate, that is both names default effectively simultaneously, with the definition given as:

(3)		 
  
Default correlation, however, is used in this model as an input, resulting in the joint hazard rate being given by
(4)		 .			

In order to find the joint hazard curve, the default correlation is first estimated by adopting the CreditMetrics methodology.  Assuming the asset correlation between two obligors is  , the joint default probability defined by the CreditMetrics reads

(5)	 ,

where   is the cumulative normal distribution function. On the other hand, the joint default probability, defined in the framework of multivariate Poisson processes, is expressed as

(6)	  

By combing Eqs (5) and (6), we can solve for

(7)		 

where

(8)		 


Once we get both the hazard rate curve for an obligor and the joint hazard curves for each pair of obligors in the collateral pool, we postulate the existence of a set of curves   which are the generators of what are termed primitive events.  These events generate defaults of single names, but also can provoke defaults of correlated names with probability  , if name   has not already defaulted.  By “generator” here, it is meant that   is the intensity of a Poisson process.  Thus the model is entirely based on Poisson event arrival, a general class of model widely used in the statistical study of reliability. 

The generators of primitive and joint credit default events are then given implicitly in terms of the inputs  and   as

(9)			 .		

From this point a triangular ansatz is used to obtain explicit formulas for the generators of primitive and joint events as
(10)			 

for  ,   for  and   for  . In the course of constructing the triangular solution using equation (10), we floor and cap the   and   to rule out unrealistic values, shown as:

(11)	 	


Once the curves for the arrival intensity of primitive events   and joint events   have been obtained, it remains to combine them in such a way as to be able to compute the expected value of default events.  For example, if we wish to compute the probability of a simultaneous default for the obligors in various subsets  , the corresponding arrival intensity can be calculated by

(12)		 ,

i.e., the sum over the names in set    of their primitive event probability multiplied by the probability of that primitive event causing a joint credit event for every other member of  , further multiplied by the probability of that the primitive event not causing a joint default event for the members of the set  .  In terms of this, one can write down generators of events for the various cases of interest for different contract structures:

 (13)			 	

The explanation of these generators is as follows.    denotes the generator of events in which name   defaults first, and by itself.  Thus LF stands for “lone first”.     is the generator of events in which the members of set   default in advance of the  members of the set  , and together.  JF stands for “joint first”.    is the generator of events in which any of the names default, either separately or jointly with any number of other names, and finally   denotes the generator of events in which name   defaults first either separately or as part of a joint credit event.  

Most credit derivatives structures rely on Monte Carlo (MC) simulation due to the difficulty of obtaining exact closed-form solutions in the manner discussed above.  In particular, the Monte Carlo approach permits the valuation of first-to-default structures taking into account the risk of default of the protection seller.  The general approach taken is the simulation of event times generated by our primitive- and joint-event generators, that is, using cumulative  to generate primitive default events and   to generate joint default events. We begin by simulating primitive event times through

(14)				 		

where

(15)				 		

The primitive event times   thus obtained are then filtered through the joint event generators   to obtain default times as:
(16)			 

and then a set of default times is collected as

(17)		 
from which the value of the protection for a defined default contingent structure is calculated.

There are a variety of approaches available in the modelling of the default correlation. It has been claimed that the most widely used models in the industry are based on the copula approach.  

A copula is a mathematical function that combines marginal probability into a joint distribution. For n uniform random variables,  , the joint distribution function is defined as

(18)		 

which is called Copula function.

The normal copula function is a multivariate cumulative normal distribution with correlation matrix  . Applying the normal copula function to the modeling of correlated default events of a collateral asset pool, the uniform random variables are mapped to the default probabilities with standard normal distribution. The normal copula function, or the cumulative joint default probability for the collateral pool with n assets, can be expressed as

(19)  

where   is the standard cumulative normal distribution function.

With the joint distribution described by the multivariate normal distribution, the correlated default times can be calculated by either closed form solution or by Monte Carlo simulation. The details of the copula model can be found in the cited papers.

As indicated from above to subsections, the model is quite different from normal copula approach in modelling default correlation. Both have advantages and disadvantages, as discussed by Josh DanzigerError! Bookmark not defined.. Actually there is intense academic research in the field of default correlation. To the best of our knowledge, there is no solid conclusion yet and it is quite possible that there won’t be solely one correct answer in the future. However, due to the popularity of normal copula model, it is still interesting to compare it with our model. We will show our comparison results in the next section.

The credit derivatives can be treated in a two-leg fashion: fee leg and protection leg. The protection buyer of the pays a fee to the seller periodically of the protection in exchange for a contingent payment in the event that the reference obligor(s) default before the maturity of the trade. If the reference entity is a collateral pool, the default events of the obligors are correlated and should be modelled by default correlation model.

The CDS with counterparty risk is a credit derivative in which we could recovery certain fraction of the forward contract value, if the counterparty defaults before the reference obligor.  

Assume that a protection buyer signs a CDS contract with underlying reference obligor 1 and the counterparty 2, we have the value of credit protection under this model to be

(20)	 
where the use of   indicates that we are considering only the case where the reference obligor always defaults before the counterparty.  D(t) is the discount factor and the notional is set to be 1. Adding recovery from the counterparty results in the following formula

(21)		 

which can be interpreted as the expected value of the protection in the case that the reference obligor defaults alone plus the expected value of protection in the case that both the reference obligor and the counterparty default, with recovery rate   expected from the  protection seller.
Together with the fee leg with the cash flow at intervals  (maturity), the B/E spread is then expressed as

(22)		 


Payment for the fee during the period   is made at   if default has not occurred.   is the day count fraction.	

One important type of credit contingent structure is the first-to-default basket.   Here the generator of “absolute first” events is important.  It is important to note that the model supplied includes a closed-form solution for this type of structure only in the case of a risk-free protection seller.  The value of the protection in this case is given as

(23)			 

for a basket consisting of  names.

In a FirstNofM basket swap ( , where m is the number of obligors), there is a contingent payment at the nth default event and the payment corresponds to the non-recovered part of notional under the corresponding obligor. 

In model, there is no closed form solution for FirstNofM contract and we have to rely on Monte Carlo simulation for pricing. 

The FirstLoss contract is a synthetic collateral debt obligation (CDO) with the structure shown in Figure 1. The underlying collateral pool, which is consisted of obligors, is mapped to a prioritized collection of tranches. The default events of the obligors in the pool would trigger contingent payments by the tranche seller in such a fashion that a senior tranche could be hit only after all the tranches junior to it have been exhausted.  In the model MC simulation has to be used to price the FirstLoss trade.


Figure 1  FirstLoss Trade – synthetic CDO





There have been two principal modifications.  The first is to change the manner in which asset correlations are converted into default correlations. Instead of one fixed period conversion, the coversion is computed at each time point for which there is a change in the hazard rate curve. The second change is that   and  are floored to zero and   is capped to one to rule out the possible unrealistic values, which would lead to the crash of the model. 

Both changes are consistent with the underlying assumptions of the model. The model becomes more robust after the improvements are made.

There are no criteria to verify the default correlation model directly. However, there are certain basic theoretical restrictions that every default correlation model should meet. Ones we employed to test are:

A.	Whatever the correlation model is, the unconditional default probability should remain unchanged if the correlation changes. Because the unconditional default probability, which is described by the hazard rate curve, severs as the inputs of the model, it is straightforward to test this assumption.

B.	Default correlation models should approach same limits under certain circumstances, if the correlation is one and zero. When the asset correlation is zero, each obligor is independent and there is no correlated default event at all. Hence the multivariate distribution is simply the multiple of that of all obligors, which should be same for any default correlation model.  On the other hand, if the obligors are assumed to be homogenous and the asset correlation is assumed to be one, all the obligors in the collateral pool are perfectly correlated and should behave like one obligor. In a scenario either all the obligors default at the same time or no one defaults.  

We assume that the hazard rates for each obligor in a collateral pool with 10 obligors is 0.2 flat. First, the unconditional default probability for one test obligor is examined.  The default probabilities of the test obligor within 5 years and 10 years with different correlation are shown in Table 1.a. With the correlation being 0.3, the default probabilities of the test obligor within 5 years and 10 years with different random seed are shown in Table 1.b.  The theoretical default probability can be calculated:

(24)	 

It is shown in Tables 1.a and 1.b that the results generated by MC simulation using default correlation model meet the theoretical value quite well as the correlation changes. 

It should be noted that, as shown in the above section, in the model the MC is not directly based on the hazard rate but instead relies on   and . Hence it is not trivial to check the unconditional default probability generated by the model. From this viewpoint, this test also verifies one basic assumption concerning multivariate Poisson process.

Given the same collateral pool, we calculate the default probabilities for any obligor default within 5 years, when the correlation changes. The results, calculated by employing model and normal copula model, respectively, are plotted in Figure 2. 

In the limit of correlation 0 and 1, the theoretical value of the default probability of any obligor reads:

(25)	 


The default correlation model and four credit derivative models contingent on the correlated defaults of the underlying collateral pool have been investigated in the re-review of the second phase of the model. Test results show that the model is consistent with the models and implemented correctly.

The model and the normal copula model are different in theory and implementation. The methodology employed in the model is based on multivariate Poisson process, which is simple and robust in predicting correlated default events. Tests have shown that the model meets the perquisites and theoretical limits for default correlation models. In fact the default correlation model has been the centre of research for a long time and every model has advantages and disadvantages.  For a typical collateral pool observed in the industry, most models behave similarly with a slight quantitative difference in predicting joint default probability within a typical 5-year term upon which most current credit derivates are dependent. 

In the model the single name CDS and the FTD basket are priced using the closed form solutions while the NofM baskets and the FirstLoss are priced by employing MC simulation.  In order to verify these pricing model, various tests are designed which include comparing the results between the MC simulation and the closed form solution whenever available, verifying the trend of the model with business rational and theoretical limit, and cross checking by replicating one trade with another trade model whenever available. The test results indicate that the pricing models are implemented correctly and meet the purpose they are deemed to serve.


Reference:

https://finpricing.com/knowledge.html

