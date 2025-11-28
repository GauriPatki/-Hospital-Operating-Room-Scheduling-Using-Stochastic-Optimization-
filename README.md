# Hospital Operating Room Scheduling Using Stochastic Optimization
 “Optimization of surgery sequencing and scheduling decisions under uncertainty” by Brian Denton
 · James Viapiano · Andrea Vogl)
 
 The project addresses the challenge of efficiently scheduling surgeries in hospital operating rooms (ORs) amid the uncertainty of surgery durations. This uncertainty leads to operational complexities, including unanticipated delays that can cause cascading effects such as extended wait timesfor surgeons and patients, underutilization of OR staff, and increased overtime costs. Improving scheduling accuracy and efficiency can help optimize resource utilization, minimize delays, and reduce operational expenses, thereby enhancing both patient care and hospital performance. The primary optimization problem involves finding an optimal sequence and start time for each surgery in the OR schedule to minimize combined costs. These costs include surgeon waiting time, OR team idling, and overtime costs, all of which vary depending on the sequence and timing due to unpredictable surgery durations. The project employs a two stage stochastic linear programming model with binary decision variables to determine optimal sequencing and continuous variables to fine-tune start times, seeking a balance between operational efficiency and cost control.
 
# 1. Datesets
Dataset 1 : The dataset used for this project is a sample extracted from a larger dataset, specifically selected to represent surgery scheduling in a single operating room (OR). For the purposes of this analysis, only data related to one operating room (OR8) is considered, simplifying the complexity while still offering meaningful insights. The dataset was sourced from reginfo.gov and includes modified timings for surgical procedures. 
 
This dataset captures various elements related to surgery scheduling, providing a sample of patients, surgeries, and timings. It allows for the analysis of how surgeries are scheduled in a single operating room, focusing on the variability in start and end times, and the potential for operational inefficiencies such as delays, idle OR staff time, and longer waiting times for patients.

Dataset 2: This dataset is utilized to calculate the waiting and idling time costs associated with the surgical operations. It represents a typical surgical team consisting of 10 members, each playing a specific role during the surgery. The dataset includes the average hourly pay for each team member, which has been sourced and compiled from reputable platforms such as PayScale.com and ZipRecruiter.com.


#  Cost Variables Setup:
cw represents the waiting cost, which reflects the average hourly wage of surgeons or OR staff. This cost is calculated as the sum of the average wages for all staff, represented by staff["Average($)"].sum().
cs represents the idling cost, which is the cost associated with an unused operating room, such as maintenance, electricity, and other overheads. This is set to $37 per minute, which is considered the average rate for OR idling costs.
c represents the tardiness cost, incurred if surgeries run over their scheduled times. This cost is set to reflect overtime pay or penalties for exceeding the scheduled time, with the average overtime pay calculated as 1.5 times the hourly wage of the staff, which is also an average universal rate for
 overtime calculation.
Finally, M is a large constant, set to 10,000, often used in optimization problems to enforce constraints or ensure certain conditions hold in the model.


# Heuristic 1 (H1): “Sequence surgeries within each block of cases in order of increasing mean of durations.” 
This heuristic sequences surgeries within each operating room by first calculating the mean duration for each room. Surgeries are then sorted by operating room, followed by mean duration, and individual surgery duration in ascending order. This helps prioritize surgeries within each block to improve scheduling efficiency.

# ModelType: 2-Stage Stochastic MIP model
We formulate a two stage problem where the first stage decision variables focus on the determination of start times for the surgeries, and the second stage addresses the ordering of surgeries within the operating room. The model assumes a discrete, finite set of scenarios, denoted by {𝜔ₖ ∣ 𝑘 = 1,…, 𝐾}, which represent the uncertainty in surgery durations. 
These scenarios are generated to reflect potential variations in durations, modeled through statistical sampling. The first stage decisions are made with limited knowledge of the future outcomes, while the second stage involves making adjustments based on the realized scenario.
Given this discrete set of scenarios, we can write the deterministic equivalent of the two stage recourse problem using a sample average approximation.

# Conclusion:
• The implementation of stochastic scheduling has proven to be a valuable tool in optimizing operating room (OR) efficiency and reducing costs.
• Our results highlight that the common practice of scheduling longer and more complex cases earlier in the day can negatively impact OR performance metrics, such as utilization and turnover time.
• By incorporating variability and uncertainty in the scheduling process, the stochastic model enables a more flexible and cost-effective approach, leading to a significant improvement in performance.
• The values of stochastic model (Model 1) and the deterministic model (Model 2) demonstrate a clear advantage.
• The Value of the Stochastic Solution (VSS) further emphasizes the cost savings and performance improvements achievable through stochastic scheduling, making it a highly effective strategy for optimizing OR resource management and minimizing operational costs.
 
