# MIST4610Project1
MIST 4610 Project 1 Group 1 Srinivasan Fall 2025

# Team Name:
Group 1 

# Team Members:
1. Pragnya Nallagonda [@PragnyaNal](https://github.com/PragnyaNal)
2. Carter Trent https://github.com/mct29403
3. Kohan Davis https://github.com/krd90067
4. Eric Mied https://github.com/ericmied

# Problem Description:
Our goal was to build a database storing information for a specific fight night, that exhibits a set group of fighters. The main entity is the fights and we aim to store data to organize and efficiently compare aspects of the fights. To compare and provide further insight into the data we plan to use queries to filter the data into information.

# Data Model
The highest entity in our model is the event entity. Each eventID represents each fight card or tournament organized by the company, containing information such as event name, date, location, and promotion details. Since each event has multiple fights but a single fight cannot be a part of multiple events it is a one to many relationship.

The Fight entity is central to the model and represents each individual bout that takes place within an event. Each fight includes information such as round schedule, fight result, and the two fighters who compete. Because one fight involves two fighters and a fighter can participate in many fights, the Fight table has two foreign keys referencing the Fighter table to distinguish between competitors. The Fight entity also connects to the Referee, Judge, and FightResult entities, allowing the system to capture the full administrative and scoring details of each bout.

The Fighter entity stores biographical and competitive data about each athlete, including name, nationality, date of birth, height, and weight. Each fighter belongs to a specific WeightClass, establishing a many-to-one relationship between Fighter and WeightClass. Fighters are also associated with a Gym, which represents the training facility or team they belong to. The Gym entity contains gym name and location information and has a one-to-many relationship with the Fighter entity, since each gym can have many fighters.

To record the outcome of each fight, the FightResult entity stores details such as the method of victory, round and time ended, and result description. This data provides transparency for how fights are won or lost. Similarly, the FightJudgeScore entity serves as an associative entity between Fight and Judge, representing the scores assigned by each judge for a specific fight. This allows multiple judges to evaluate the same bout independently, with each score tied to both a judge and a fight.

The Referee entity stores information about referees who oversee fights, and each referee can officiate multiple fights, creating a one-to-many relationship between Referee and Fight.

Finally, the Sponsorship entity represents commercial partnerships between fighters and brands. Each sponsorship record includes brand name, contract start and end dates, and the associated fighter, establishing a many-to-one relationship between Sponsorship and Fighter.

<img width="1019" height="333" alt="image" src="https://github.com/user-attachments/assets/8e68f983-1707-4d3c-a704-ff39a346fc62" />

# Data Dictionary
<img width="532" height="635" alt="Screenshot 2025-10-21 161653" src="https://github.com/user-attachments/assets/6b36c2aa-f7f0-41e1-83b0-65ebdb701867" />
<img width="531" height="661" alt="Screenshot 2025-10-21 161704" src="https://github.com/user-attachments/assets/89dfbba6-ab26-4269-9366-ab2624beb6d6" />
<img width="529" height="571" alt="Screenshot 2025-10-21 161710" src="https://github.com/user-attachments/assets/dca3ed63-4681-4c2e-847c-dda19e2f6e67" />
<img width="540" height="385" alt="Screenshot 2025-10-21 161715" src="https://github.com/user-attachments/assets/de72c664-8793-476b-8394-be77d69b54de" />


# Queries
1. Query 1 lists the event details for the fight nights. This list includes the EventID, EventName, EventDate, EventLocation, and EventPromotion. Query 1 allows managers to see important logistical informaiton in terms of each fight night. Knowing information like event date and location will be important for predicting revenue for the fight night as well as being important information for planning the events.

   <img width="632" height="220" alt="image" src="https://github.com/user-attachments/assets/9a683579-3c0d-4dcb-add1-c34a6f8bf0b5" />

2. Query 2 alphabetizes the fighters participating in the fight nights. This query includes FighterID, and the fighters first and last name. Query 2 allows for managers to get important information like the fighters names to people running the event such as promoters, as well as announcers for fight commentary.

    <img width="480" height="267" alt="image" src="https://github.com/user-attachments/assets/354eaa96-2eb4-4501-a09a-3bb89982148e" />

3. Query 3 lists the weight classes used in mixed martial arts. This query includes weight class ID, the weight class name, and the max weight allowed for each weight class. This is important information for the manager as it allows them to see what weight class each fighter in the fight night is in. It also allows for guidelines within the sport and ensures that each fighter is in the correct weight class at weigh-ins.

    <img width="447" height="348" alt="image" src="https://github.com/user-attachments/assets/a16c3e06-b626-4c4a-b5fa-7148097bd1fc" />

4. Query 4 lists the gyms that the fighters in the event train at. Included in this query is the gym ID, gym name, and gym location. This query allows managers to see the different gyms each fighter has trained at. Gyms can be influential on a fighter as each gym has different coaches and different techniques that may be taught there that might influence a fight. This information is also important for announcers as it may influence some of their dialogue during the fight.

   <img width="337" height="260" alt="image" src="https://github.com/user-attachments/assets/abeef0de-df26-4b8e-8fad-24f5cb4d3576" />

5. Query 5 flags fighters over their class limit. It returns FighterID, name, FighterWeight, and the class max from a correlated subquery. This is a compliance and safety check before weigh-ins. Managers can act early: reclassify a bout, schedule catchweights, or issue fines. It also helps coaches manage cut plans and reduces last-minute cancellations.

    <img width="966" height="312" alt="IMG_3231" src="https://github.com/user-attachments/assets/75fc9da8-0914-4dba-984e-6c36e5642d4c" />

6. Query 6 finds gyms with at least two rostered fighters using GROUP BY + HAVING. This highlights partner gyms with deeper ties to the promotion. Useful for outreach, comp tickets, media day invites, and negotiating cross promotions. It also signals where on-site hand-holding helps, since multiple athletes from the same gym may need staggered medicals and transport.
   
    <img width="627" height="281" alt="IMG_8273" src="https://github.com/user-attachments/assets/ee27915d-fb57-476b-8d92-f3908da09690" />

7. Query 7 lists events with more than one fight. It gives an immediate filter for true cards vs. single exhibitions. Operations can validate staffing levels, medical coverage, and broadcast blocks. Finance can forecast gate and concessions based on bout count. Marketing can prioritize multi-fight cards for ad spend.

     <img width="643" height="285" alt="IMG_1524" src="https://github.com/user-attachments/assets/b4da4921-c0e0-4674-8e02-c4659e0662fc" />

8. Query 8 shows fighter counts per weight class, sorted by depth. This informs matchmakers where divisions are healthy vs. thin. Use it to plan talent scouting, contender series slots, or to avoid over-booking shallow divisions. It also helps set tournament formats and belt defenses with enough bench strength.

     <img width="685" height="287" alt="IMG_8506" src="https://github.com/user-attachments/assets/99ae3468-b7a4-4e5a-a4aa-873048fc5c02" />

9. Query 9 summarizes sponsorships per fighter and earliest start date. Managers can see who is marketable now, who has brand history, and where to pitch new deals. It supports revenue sharing audits and avoids contract conflicts. Earliest start date also hints at brand loyalty that can be leveraged for renewals.

     <img width="1148" height="302" alt="IMG_5319" src="https://github.com/user-attachments/assets/9096bb7d-eb24-49df-b0d2-05358e2465bf" />
   
10. Query 10 provides height and weight stats per class: min, max, and averages. Matchmakers can balance reach/size dynamics across a card. Performance staff can spot outliers that may need tailored nutrition or conditioning. Broadcasters get clean talking points about the division’s body type profile.

     <img width="916" height="337" alt="IMG_1378" src="https://github.com/user-attachments/assets/f99a4e10-5e5f-4b20-a10d-dc6af21d9c2c" />

# Database information
Name of the database: ns_F25MIST4610_15058_Group1
Additional information: Each query listed above is marked in the database using stored procedures which can be called using the following format: CALL TP_Q1();
