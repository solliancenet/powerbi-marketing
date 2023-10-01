# Bartek Ingredients - data and report modeling

-   Last updated: 11/8/2022

## Document purpose

This document provides an overview of the existing business domain, user
personas, and related IT artifacts. It allows Solliance to understand
the current environment quickly, suggest areas of improvement that may
be a better fit for the organization, and envision the possibilities.
The client and Solliance can be better aligned moving forward. Once the
project team decides on the priority areas, a roadmap can be created
encompassing the goals. The document content will be updated as more
knowledge is shared in various meetings. The information is a snapshot
in time and is not meant to be perfect. The goal is to gain initial
context to make the team more efficient and ensure the deliverables mesh
with the current organizational culture. This type of alignment helps
avoid rework. The document's target audience is the project Data AI
developers. Descriptions are meant to be brief and fragmented. Goal -
disseminate information fast.

## Business background

Bartek Ingredients is a specialty chemical manufacturer serving food &
beverage and industrial end markets. Established in 1969, Bartek
Ingredients Inc. is a leading producer of malic acid, fumaric acid, and
maleic anhydride. Headquartered in Stoney Creek, Ontario, Canada, Bartek
employs 120 people across its two production facilities in Southern
Ontario. Bartek's facilities are registered to the ISO 9001:2015
Standard. Bartek also holds the BRC Global Standard for Food Safety
certification, and it distributes to more than 40 countries around the
world. For more information about Bartek, visit bartek.ca.

-   Malic & food-grade fumaric acid, pectin (classified as a chemical
    manufacturer)
-   What is the metric that drives business **success**? e.g. Product
    pounds shipped per time period. This month, quarter, and year.
    -   Netback/lb shipped
    -   Production output
    -   BOM/Processing Chemicals
    -   Fully absorbed cost/lb of indirects
-   Employee count: 160

## Business domains

-   Customer delivery engagement
-   Engineering
-   Inventory management
-   Production/Process Management
-   Quality
-   Sales

## Describe how customer purchase products or services

-   How do they place orders?
    -   Product group and granularity. Pounds.
-   What is the average delivery fulfillment duration? Parameters?

## Basic Bartek production order process

Maleic Anhydride is created in batches. Each batch **could** go through
a 23 step process. Depends on the batch.

-   Step 6 is a very important step. Pot temperature and pressure is
    measured.

-   Step 20, 21, 22 are not tracked all of the time. Depends on the
    batch being produced.

> Note: Confirm with client.

P1 Production Orders are managed through an internally developed power
app - Released Production Orders are synched to dataverse and then
queried for the production app - Packagers sign off each pallet as
produced - QA & WH signoff is also tracked with an app

## Project background

-   What is this phase reporting focus? Strategic or operations? Revenue
    or expense?
    -   Operations
    -   Shiptments and Netback
-   How long did it take to create the reports?
    -   Most of the current content was created over the past 6 months

## Other background information

-   Two production plants
-   One to be commissioned
-   One to be decommissioned
-   The new plant will be completed in Q1 2024 and will double the
    company's existing capacity.

### Other operation background information

-   Bartek can store 2 days of butane. If there is outage in trucking.
    Bartek will be shutdown in 2 days.

> TODO: What is the plant name or symbol? - There is a Bartek plant that
> makes the raw material Maleic Anhydride. It has a storage tank of 1
> million pounds. The plant makes 180k pounds a day. It can store 5 - 7
> days of material. There is a merchant market this could be shipped to.
> Spot market is thin. No guarantee to ship out of the tank. - The other
> plant can store an additional 5 days. - There is another plant that
> draws the raw material down and produces the finished product. -
> Bartek needs to draw down the materials at the rate of production.
> Otherwise, Bartek needs to generate merchant market sales.

## Organization questions answered using business intelligence/analytics

Reports are meant reduce the amount of time required to make business
decisions and drive users to action. Most reports have an initial
question or premise in mind.

### Current questions answered

-   Strategic

    TODO: Discuss with Bartek

    -   Are the plants in balance (output of P2 in line with draw of
        P1/P3)
    -   Are supply and demand in balance
        -   Sales forecast in line with production forecast and
            inventory holding capacity

-   Operational

1.  Production rate for each product/granulation
2.  Quality conformance (WIP/FG)
3.  Production order status (packaging/QC/WH)
4.  What is the status/projected ship date of each customer order?
5.  BOM & Processing chemical consumption monitoring
6.  MFG OH consumption/absorption
7.  Project expense tracking -- we have a bespoke dimension that is
    assigned to PO's and Journals that allows us to accumulate costs to
    projects

### Desired questions

1.  Process performance (Rate/granulation/SQC/SPC)
2.  Plant balance and projected balance
3.  Sales Variance (Rev/Qty)
4.  Cost Variance (absorption/BOM)
5.  How long does it take to move from one stage to another stage?
    e.g. Ready to ship to Shipped.
6.  What is the average off-spec metric per product? What the threshold?
    What actions are taken?
7.  What is the average time required to fill an order?
8.  What is the average profit per product?

> TODO: Confirm these questions.

### Questions for Bartek

1.  What are the organizational production goals this year? in-process
2.  What do you consider early warning signals? plants operating at
    different rates.
3.  What is the industry standard order to ship duration? Not a
    priority.
4.  What are your workflow opportunities for improvement? How are you
    measuring them?
    -   Using WIP QA data to minimize off spec
5.  How are you measuring KPI growth?
    -   Volume and Selling Price
    -   Production rate and cost per unit
6.  What is the industry spoil rate?
7.  Do you have any key metrics you are trying to optimize?
    -   Conformance to production forecast
    -   Butane yields (in Maleic Anhydride production)
    -   MEA yield (in malic and cofa production)
8.  What does MOD_RC mean? Modified release code? How is it used?
    -   We use these codes to identify off-spec conditions that limit
        the customers who can take a given product (high fine particles
        is a common Mod RC)
9.  Do you have a plant layout and codes associated with location areas
    in the warehouse/plant?
    -   no we only have facility level codes

## Current environment challenges and concerns

-   What is the current report user creation and change adoption
    process?
-   Users want the data refreshed faster. Scheduled refreshes takes 30
    minutes to refresh. 30-minute old data is useless to the operations
    team.
-   Data model reuse.
-   Report data trust
    -   Data model validation and governance.
-   Data flow/refresh monitoring
-   Business logic spread. Business logic changes will create friction
    as many things need to change.
-   Missing a change leads to inconsistent data and trust issues
-   Cleaning the same data on a repeated basis for multiple datasets is
    not efficient
-   Bugs can be re-introduced during changes
-   Mapping legacy to current data is required for any BI solution.
    -   TODO: Explore the associated business reasons and costs.

### Project concerns

-   Steven is concerned Power BI dataset models cannot be consumed and
    used in Excel very easily. He needs to understand the process and
    verify this solution will work.

> TODO: Confirm

![](media/2022-10-27-17-19-31.png)

### Predicted challenges

-   Data source schema changes
-   SaaS LOB insulation. Bartek needs the ability and path to switch
    SaaS vendors without losing the ability to capture and report on
    critical operational data.

#### Data and reporting accuracy

-   What is the perceived and measured data and reporting accuracy? Is
    there a current tool to capture user requests and errors? Tie the
    requests to a report or data area.

### Report user working teams

1.  Commercial sales
2.  Plant production
3.  Executive leadership

## Project stakeholders

### Bartek

-   Steven Chambers - CFO - steven.chambers@bartek.ca
-   Eric Turner - Senior Analyst, Advanced Analytics -
    eric.turner@bartek.ca
-   Kamil Salagan - Manager, Infrastructure & IT -
    kamil.salagan@bartek.ca

### Solliance

-   Lino Tadros - IoT lead
-   Dan Patrick - Infrastructure lead
-   Carey Payette - Azure Synapse Analytics lead
-   Ike Ellis - Lead and Data AI architect
-   Tim Henning - Power BI Developer - timh@solliance.net

### Communication preferences

-   Teams?

## Initial general observations

Creating good BI reports and artifacts is all about iterating and
refining your model and reports. Based on your previous efforts, you
know more about your users' reporting needs and what can be improved.
You have learned. As part of your improvements, you need to figure out
how to make the current assets maintainable and performant to meet the
next set of business requirements.

The goal is not to provide a rating of the current state because there
is always a better architecture or report. For example, Power BI is
updated every month to meet the changing business demands. It has
evolved over the years and so should your architecture, designs, and
reports. The better question to ask, "Does the current BI assets meet
your current business needs and can it scale to your future
requirements?"

### Current architecture and solution considerations

1.  Does the current solution provide the answers the business requires?
2.  Does the solution fit the organization and project budget?
3.  Will the solution scale and provide sufficient performance to meet
    the upcoming needs?
4.  Can the current operations and development team maintain and expand
    the proposed architecture?
5.  Are the organizational users happy with the reports?

### Current BI assets

The current BI team has created many Power BI reports. There is a
fundamental understanding of how the tools work and the development
process. The Solliance team can assist in refining the processes and
provide suggestions on best practices.

> TODO: Based on the existing data models and reports, the Solliance
> team would like to understand any data insights learned so far.

### Types of analytical reporting

1.  **Descriptive** - Data assessment and exploration - surfacing data
    beginning aggregation or curation. Addressing basic organization
    reporting needs. Determining data granularity. What attributes drive
    the measure values. Descriptive analytics - what has happened in the
    past. Start to begin data monitoring based on priority.
    Understanding the data thresholds. Min, max, and averages. Report
    filtering can be fine tuned allowing for a personalized view of the
    data. Alerts can be created based on priority values that land
    outside the thresholds.
2.  **Diagnostic** - Why did this happen? Determine causation and
    effects.
3.  **Forecasting/predictive** - Requires an excellent understanding of
    the data and dependent processes. Using historical data and trends,
    the organization would like to predict future values and understand
    the probability of occurrence.
4.  **Prescriptive** - based on option analysis, what actions should be
    taken. View and recommend the best course of action before making
    decisions.

#### Initial thoughts

-   The current reports are descriptive in nature.
-   It seems like the team is exploring the data and determining
    questions that could be easily answered.
-   Using target goals in Process (Unified). Perhaps move the goals to a
    central dataset.

> TODO: Confirm

### Requirements gathering process

Initially, there will be a lot of assumptions and questions that need be
verified and answered. Solliance needs enough time to explore the
current reports and data to provide some options to iterate from and
gain inspiration - gain context.

-   What is the main purpose of each report and what are the insights
    gained so far?

> TODO: Need report review working sessions.

### Data modeling

#### Main data lineage

Using chained/layered datasets. Looks like the strategy is to use
UnifiedDataModel as the datamart. The current set of datasets don't have
many measures. Lots of calculated columns.

![](media/2022-11-02-17-27-31.png)

#### Database

-   **Make use of database schemas** segment the data and protect the
    data warehouse tables. Associate objects with general organization
    usage and semantics. Generally, schema names should not change
    frequently. It does provide a clues as to the intended usage and the
    teams to consult. Separate permissions can be applied to schemas. It
    can prevent accidental updates to views, stored procedures, and
    functions.
-   **Limit the data and set the interface using views**. Instead of
    pulling in large wide fact tables, consider creating database view
    that solves your reporting needs. Save time by reducing the data
    transformation steps in PowerQuery. Insulate the model from future
    database field and table name changes.

#### Current Power BI Data modeling observations

Example PBIX - UnifiedDataModel - In memory size is not huge. Lots of
tables and columns. Those could be reduced. The smaller the model, the
better the performance.

    ![](media/2022-11-05-07-48-07.png)

-   Inconsistent naming conventions.

    ![](media/2022-10-23-10-53-19.png)

    > Reason: - **Inconsistent field and table naming conventions**.
    > This makes it difficult for other developers and the user
    > community to quickly leverage the model. Inconsistency leads to
    > errors and increased QA time. Users may not have the patience to
    > learn the model and incorrect results leads to model abandonment.

-   Many to many relationships

    ![](./media/many-to-many-relationships.png)

    > Reason: Which table do I use for additional reporting and
    > filtering? Report builders will get confused. When you want to
    > create a slicer, you suffer a performance problem because now you
    > have scan the whole fact table to find the distinct values. And
    > you are not sure you got all of the values for that dimension.
    > What happens of one fact table has some values the other fact does
    > not have? Your slicer or filter context will not be complete. It
    > makes creating measures difficult later. You will get varying
    > results. **Consider creating a new shared dimension table and
    > relating the two fact tables**. Exception to this rule: Depends on
    > how you slice your data. Do you have a bridge table? You will need
    > to test.

    > Note: Need to understand the usage context and the data.

-   Bi-directional relations

    ![](./media/bi-directional-relationship.png)

    > Reason: Computing values in measures will be unpredictable. Use it
    > sparingly. Transforms the model. Creates ambiguous relationships
    > that can lead to a circular dependency error. A table with
    > multiple relationship paths to another table is said to have an
    > ambiguous relationship. Which path will the engine take to query
    > related data? You cannot be sure. Will the aggregate totals be
    > correct? You have to remember to remove relationships in your DAX
    > code explicitly to force the desired path.

    > Note: Need to understand the usage context and the data.

-   Blank values

    ![](./media/blank-values.png)

    > Reason: Blank/space values in your slicer usually indicate there
    > is a referential integrity data issue in one of your fact
    > dimension relationships. This could lead to incorrect totals and
    > aggregate measure values. You have to remember to turn on items
    > that have no value. Power BI will insert an artificial row,
    > depending on the function. For example, VALUES will contain the
    > values, plus the blank row. Table references will not count the
    > blank rows. DISTINCT does not compute blank values. ALL references
    > the blank rows. COUNTROWS, by default, does not consider the blank
    > row. Better to fix the data and invalid relationships. Filtering
    > out blank rows may be returning invalid data. Blank rows can also
    > cause circular dependencies. You need to replace functions that
    > reference blank rows. For example, replace ALL and VALUES with
    > ALLNOBLANKROW and DISTINCT.

-   Relationship data might not match

    ![](media/2022-10-23-10-51-30.png)

    > Reason: Incorrect relationships will produce undesired or
    > incorrect reporting results.

-   Relationship keys are not integers

    > Reason: Relationships built on integers perform much better than
    > text values.

-   Hide foreign keys away from report creators.

-   Using a lot of date hierarchies

    ![](media/2022-10-31-11-37-31.png)

    > Reason: Using more storage than necessary. Power BI is going to
    > take longer to refresh the data that you might not be using.

-   Need to mark date tables as a date table. Performance reasons.

    ![](media/2022-10-31-11-40-26.png)

    > Reason: When using the date table, the relationships are based on
    > a date a column and data type. The Vertipaq engine automatically
    > removes the filters for appropriate time-based calculations. Using
    > any other type of data type, like integer, it will not
    > automatically removed. Your calculations might be incorrect.

-   Multiple workspaces might help with organization and process

    ![](media/2022-10-31-15-27-28.png)

    At a minimum, you should have a DEV and PROD workspace. You will
    want to limit the amount of development in personal workspaces.

-   Consider breaking out time away from timestamp

    ![](media/2022-11-02-17-34-23.png)

    > Reason: You get better performance and data compression when your
    > values are not unique. For example, 11/19/2021 is found 4 times
    > but could be stored once in memory. 4th hour could be stored once
    > in the time value could be stored once. Each of the columns are
    > stored separately in memory. Vertipaq converts your table columns
    > using compression algorithms - Dictionary/hash compression, value
    > encoding, and run-length encoding. Also, if you split your data
    > into additional columns, the Vertipaq engine will eliminate
    > columns that are not part of the query constraints giving you
    > better performance.

-   Consider using date data type instead of date/time

    ![](media/2022-11-02-17-48-14.png)

    > Reason: Better performance. Taking up more space in memory.

-   Fields only have one value in the table. No variation in data.
    Recommendation - Remove from the model.

    ![](media/2022-11-04-06-47-00.png)

-   Vertipaq database analyzer

    ![](media/2022-11-04-09-50-55.png)

    -   It seems like you could gain some efficiencies by removing some
        unnecessary columns. For example, you have 81 and 99 columns in
        your biggest tables. The columnar database engine likes long
        skinny tables. Vertipaq is storing each of these columns in
        separate files, whether you are using them or not. Before the
        Vertipaq loads the model and data into memory, it needs to test
        the best sort order on the columns. Contiguous repeated values
        in a column gets compressed. Vertipaq is testing the best
        sorting options for the columns. The more columns you have, the
        harder the Vertipaq engine has to work to find the optimal sort
        order. Sometimes it will timeout and choose a sort order. This
        is why you should removed unused columns.

    -   Segmentation - None of the tables are over a million rows.

    ![](media/2022-11-04-09-49-55.png)

    -   Split your date and time values in different columns. You can
        get better compression and performance.

    ![](media/2022-11-04-16-03-53.png)

    -   High cardinality relationships can lead to poor performing
        queries. Cardinality: Object cardinality; the number of rows in
        a table or the number of unique values in a column, depending on
        the level of detail in the report.

    ![](media/2022-11-04-16-15-15.png)

    > Note: Confirm understanding.

-   High amounts of calculated columns

    ![](media/2022-11-05-09-33-50.png)

    > Reason: The Vertipaq engine performs better with fewer columns and
    > many rows. Calculated columns are necessary row bound calculated
    > data, which can be useful for slicers, and row
    > categorization/grouping. However, every time you refresh your
    > data, all of your calculated columns have to be refreshed as well.
    > **This can adversely affect refresh time**. Additional storage is
    > used for the column. Do you need to pre-compute these values for
    > performance reasons? A calculated column uses RAM instead of
    > runtime CPU. Additional review is required. We don't need to worry
    > as much for smaller tables. Tables that will grow considerably
    > need to be examined more closely.

-   Need to format your DAX code

    Unformatted ![](media/2022-11-08-11-04-39.png)

    Formatted ![](media/2022-11-08-11-03-21.png)

    > Reason: Makes it easier to debug and maintain.

### Visualization observations

Data visualization helps you to focus on the meaning of data, rather
than looking at the data itself. A good data visualization enables you
to quickly spot trends, anomalies, and potential issues.

Dashboard is a day-to-day view of KPIs, and provide the navigation point
to the detailed reports. Power BI Dashboard isn't built for slicing and
dicing.

-   **Wall of data problem.** Prevent users eyes from scanning the
    entire page to find useful information. Use other visuals to direct
    the reader to points of excellence and problems. Company is spending
    more money because the report users are not using the report
    efficiently. Time is money. Multiply the problem by the amount of
    users.

    -   Surfacing the database tables/queries in Power BI without
        driving actionable decisions.

-   **Alerts** - Not making use of key field thresholds. When problems
    arise, the user should drill down to details.

-   **Abbreviations in the report labels**. Users and developers will
    need to decode the label. Extra cognitive cycles are spent
    initially.

-   **Limit the visualizations** to 5 - 7 or less per page. Human beings
    have an 8 second attention span. Focus their attention on a question
    and group related data quickly.

-   **Use color, fonts, and whitespace to emphasize values and focus the
    attention**.

### Large datasets

-   Do any of the reports contain large datasets?

### Query parameters

-   Do any reports require parameters for data refresh?

### Incremental refreshes

-   Is the data partitioned? No.

### DirectQuery storage mode

> TODO: Confirm if any reports are using DQ.

-   Do your reports require large datasets? \> 1GB

-   Do you need up to display the most recent data?

-   Do you understand some of the limitations?

    -   For example, certain DAX functions cannot be used. Non-additive
        functions.
    -   Drill down by using year, quarter, month, or day is not
        available.

-   Every visualization is going to execute at least one query. Multiple
    users and filtering can issue many queries at once to the data
    source.

-   Using DQ in a few reports.

-   DirectQuery PBIX files

    DirectQuery storage option can produce many queries to the back end
    data source. You need to reduce the amount of queries each
    visualization sends to the database. You might want to consider
    turning off automatic filter. Was there a business need for
    DirectQuery?

    ![](media/2022-10-31-14-30-40.png)

    How to view the connections limit per data source.

    ![](media/2022-10-31-14-34-43.png)

    Power BI connections per license level

    ![](media/2022-10-31-14-35-53.png)

### Composite models

Do you have mixed data sources in one PBIX? Database and Excel?

### General data filtering and expression requirements

1.  When does the fiscal year begin?
2.  Are the report users in the same region?
3.  What are the really important date fields?

### Deferred maintenance

1.  Unused objects reports, queries, tables, fields, measures.
2.  Processes that need to be turned off or refactored?

### Other questions

1.  Are reports emailed around? Shared folders?
    -   Excel
    -   PDF
    -   Images

## Level of current and desired analytics

-   **What has happened?** Understand the causes and events. Evaluate
    data trends.
-   **What should happen in order to meet a goal?** What if parameters.
    Current state and goal comparison.
-   **What will happen?** Predictive analytics based on
    historical/industry data.

> TODO: Get client confirmation of phase goal.

## Project goals

-   Understand organization BI objectives.
-   Validate the DW structure and data.
-   Create well defined validate data marts for users to connect to via
    Excel and Power BI. The data mart would provide the well-defined
    shared data elements applications and reports could use.
-   Improve reporting data freshness for certain use cases.
-   Display critical KPI metrics in dashboards. Allow users to drill
    into the details.
    -   Manage by exception.
-   Create push notifications for high priority KPI thresholds.
-   Deprecate the old reports and/or data sources.
-   Demonstrate effective report design.

> TODO: Get client confirmation of phase goal.

### Future state report design

-   Judicious use of color to warn, inform, and emphasize
-   Trend-lines to show results of previous decisions
-   Data comparisons to goal to see length of distance left to achieve
    the goal
-   Identify outliers in visuals.
    -   Establish norms. **What does normal look like?**
    -   Was the value significantly out of the range of averages?
    -   Was there a specific production line or location the anomaly
        occurred?\
    -   Are there specific times in the week or day the occurrence is
        more likely to occur?

![](media/2022-10-27-15-43-08.png)

### Project phase domain focus

Need to effectively manage the business. Focus on Dataverse and ERP data
and analytics. - Steven

-   Inventory the business questions current answered and that need to
    be answered via analytics.

-   Inventory existing reports and document use cases.

-   Determine business domains focus. Mock up reports based on existing
    reports and desired improvements. \>TODO: Why are the users
    downloading the report data source? **Review user community created
    reports**. What questions are they answering with the data?

-   Use new reports to validate the DW data pipelines, structure, and
    data. Compare new reports with existing reports.

-   Deprecate the old reports and/or data sources.

-   **Steven would like to focus plant balancing**.

    -   Top level dashboard that shows the butane inventory. Production
        rate of P2. Inventory between the plants. Average draw rate of
        P1. Are the production and draw rates in balance. How many days
        until they are not in balance? Which option should Bartek
        choose? Sell raw material product or slow the plant down.
    -   Currently, this imbalance is handled through phone calls.
        Calling customers to see if they can take on more inventory.
        Logistics - calling transports to move the loads.
    -   Need the thresholds. Steven has the data quality set in Excel.
    -   When the new plant is completed, maelic storage capacity
        decreases.
    -   Benefits: Gain control of a manual process.

> TODO: Steven says he will diagram process. Also, he will send two
> Excel files. Finished Goods Quality reporting data. Planning.

## BI roadmap - 1

### Milestone possibilities

-   Architecture Design Session - data and artifact review.
-   Development team set up
-   Goal creation and curation
-   Organization prioritization alignment
-   Change communication adoption strategy
-   Identify 1 - 3 reports to drive DW model and data validation.
    Validate the data granularity.

## Initial project design decisions and assumptions

-   No need for other data aggregation and data partitioning software.
    If the dataset is less than a 1 GB, then Power BI datasets are more
    affordable. Otherwise, consider using Analysis Services. The monthly
    hosting would be affected.

-   If Bartek is interested in providing a customer BI portal interface
    for shipping status, then Power BI premium capacity might be a good
    choice. The price starts at \$4995 per month. A deeper look at the
    labor costs involved with customer shipment delivery might be
    interesting. Need to engage a representative sample of Bartek
    customers to determine interest and possible use cases. Steven
    believes document management is more of a focus for this use case.
    e.g. Certificate of Analysis. This is not the highest priority at
    the moment.

-   Going to stick with Power BI and Excel tools. It is a sunk cost and
    the other options don't provide real switching benefits based on
    Bartek's business needs.

-   We are going to focus on the ERP operational reporting needs.

## Project success factors

### High-level strategy

-   Tactical operations - Operators need reports. Need data for the
    legacy plant. Status of production orders is critical to understand
    and referenced several times a day.
-   IoT data is a different state. Separate project.

### Leadership benefit story

#### Examples

-   Business question never answered before.
-   Business question answered faster than before. Faster decision
    making capability.
-   Insights that drive increased revenue and profits.
-   Risk reduction.
-   Sales and cost forecasting. What if scenarios.

### Operational user benefit story

#### Examples

-   Fewer steps required to complete daily tasks.
-   Operational problem identified/prevented sooner.
-   Operational trends.
-   Operational forecasting. What if scenarios.

### Measurements of success

-   Capture process scorecard metrics before the project
    -   Is this information available now in BI? How long does it take
        to surface?
-   Interview stakeholders
    -   Capture key quotes related to challenges
    -   Capture how the stakeholders are making better business
        decisions
-   Report usage metrics over time
-   Feedback
-   Observed behavior change

## Project development strategy

Because Bartek has created many reports and met the targeted users
initial requirements, Steven would like to focus on the data model
first. Once the data model is created and data has ingested then he
would like to focus on the reports.

### Communication and documentation usage strategy

-   Email

-   Direct Message - Microsoft Teams

-   Status meetings

-   GitHub

-   Key decisions are stored?

### Desired development environment

-   Dev, Test, Production

TODO: Are there QA resources?

### Number of current Bartek developers

### Mix development teams?

### Tasks

1.  Identify reports that will exercise a good portion of the data
    warehouse and dataset models.
2.  Determine the data granularity
3.  Validate the data.

### Multi-layered data design

-   Land the basic data, filter it down, and transform it based on need.
    Make it possible to debug issues easily.

![](media/2022-10-27-16-48-27.png)

### Shared dataset

-   What entities and measures should be wrapped in one datasets or
    layered datasets? We need to identify domains that can be segregated
    into datasets.

### Power Query connection parameters

-   Parameterized connection. Make it easy to switch between
    environments. DEV vs TEST vs PROD.

### Shared theme file and background image

-   What are the basic colors that should be used in reports. Define
    borders, fonts, sizes, colors.
-   Background image

### Report data validation strategy

-   Read-only access to the data source helps expedite the validation
    tasks.
-   Examples of existing reports with enough data to independently
    validate new report calculations should be provided.
-   Once the report developer has verified the report draft, the report
    data validation will proceed to the appropriate Bartek resource.

### Target audience feedback

-   Existing report and use case feedback
-   Mock ups feedback

### Version control and deployment

-   Can we make use of dev workspaces? This allows the development team
    to publish and share artifacts without the users interfering.

### Large datasets

-   Review the business case for the large dataset.
-   Is the granularity necessary? Can we aggregate? Averages, etc.
-   Incremental refresh

### Pre-calculated data

-   Does it need to be dynamic or is a static calculated table
    acceptable?

### Build shared data flow

-   Tables/entities that might be shared between reports leverage Data
    Flows.

## Data Sources

![](./media/data-lineage.png)

1.  Bartek database

    -   **Server**: Websv2k12. 2014 SQL Server database.

    -   **Overview**: Database built over many years. Catch-all
        container for all types of projects. Lots of deferred
        maintenance. Some tables that are no longer being used.

    -   **Functional usage**: Raw data tables from many different
        systems. Old product heirarchy to new product heirarchy.

    -   **Client Apps**:

    -   **Example structure**:

        ![](media/2022-10-24-10-37-28.png)

2.  Bartek_BI

    -   **Server**: Websv2k12

    -   **Overview**: Used for reporting data transformation and
        cleansing. Steven Chambers is the main architect/developer. This
        database may not be used going forward.

    -   **Functional usage**: Reporting data source for existing Power
        BI and Excel reports.

    -   **Client apps**:

        -   SSIS: Currency conversion rates. Normalizes the dataset.
            Data source is Bartek, mostly. Dataset is called from Excel.
            This could be a good place to start for transformations.
            ![](media/2022-10-24-07-11-01.png)
            ![](media/2022-10-24-06-54-45.png)
            ![](media/2022-10-24-07-08-41.png)

    -   **Example structure:**

        ![](media/2022-10-24-10-39-00.png)

3.  Dataverse

    **Functional usage**: Quality data.

4.  Dynamics365BusinessCentral

    -   **Server**:
    -   **Functional usage**: Current ERP
    -   Purchase orders

![](media/2022-10-24-10-41-05.png)

4.  Common Data Service (Legacy)
    -   **Functional usage**: Legacy ERP

## Environment

## Existing networking environment

-   Co-location environment?
-   Multiple cloud providers?
-   Connection throughput
    -   On-site
    -   Off-site? VPN connections? Traveling salespeople?

![](media/2022-10-27-18-13-28.png)

## Priority dimensions

### Customer

-   Overview

### Employee

-   Overview

### System Equipment

-   Overview

### Pallet

-   Overview

### Product

-   Overview

## Priority facts

### Production

-   Overview

### Quality

-   Overview

### GL Entries

-   Overview

### Inventory

-   Overview

### Shipment

-   Overview \###

## Report user environment

### Regions

### Domains

-   Commercial sales
-   Shipping operations

> TODO: Get client confirmation of groups.

## Existing related solution tools and services

-   Excel
-   Power BI
    -   Pro licenses
    -   How did you install Power BI? Microsoft Store or a specific
        version?
-   Power BI Report Builder (Paginated reports)
-   SQL Server Analysis Services (SSAS)
-   SQL Server Server Integration Services (SSIS)
-   SQL Server Reporting Services (SSRS)
-   SQL Server
-   Common Data Services/Dataverse
    -   What application plan level?
    -   How many existing environments?
-   Microsoft Dynamics 365
-   Office 365
-   SharePoint - not implemented
-   Custom applications
    -   Chron jobs/services
    -   Workflows

## Power BI Premium capacity/user features

<https://learn.microsoft.com/en-us/power-bi/enterprise/service-premium-features>

-   Paginated reports
-   Report embedding
-   Sharing reports with non-licensed users
-   Deployment pipelines
    -   PPU/Capacity
-   Large data format

## Common terms and calculation rules

Rules that are used across many reports. The calculation needs to be
applied in a consistent manner.

### Common terms and definitions

-   Product group
-   Granulation
-   Pallet
-   Release code

### Metrics

Sales vs goal vs prior year Finance Cash flow AR Production Shipments
Workflow (Pallet Packaging)

### Slicers

-   Product Group
-   Sku
-   Granulation
-   Batch
-   Pallet
-   Date/Time - between specific dates.
-   Production Order
-   Release Code
-   Modified Release Code \## Existing applications

### Packaging App DB

-   Used in PowerApps for validation, observation & estimation
-   3.5 GB in Size. Connects to Dataverse.

## Existing reports

### Number of report users

-   4 Commercial
-   3 Admin
-   6-8 Operations

### General related report development information

-   Currency data gets converted into US dollars
-   What is the level of historical data required in Power BI datasets
    vs DW? 80/20 rule. Create datasets with 10 years?
-   Largest PBIX file size?
-   Average PBIX file size?
-   Need to map old products to new product SKU. Mapping table exists.
-   Splitting reports from dataset?
-   Using dataflows?

### Functional data structure

![](media/2022-10-27-16-28-53.png)

![](media/2022-10-27-16-31-16.png)

### Report classes

1.  P1 Environmental Report
2.  P1 Reliability Report
3.  P1 Quality Report
4.  P1 Production Report
5.  P1 Process Report
6.  P1 H&S Report
7.  P2 Environmental Report
8.  P2 Reliability Report
9.  P2 Quality Report
10. P2 Production Report
11. P2 Process Report
12. P2 H&S Report
13. Financial Reports

### Report list

## BC_FGInventory_CofA

### Overview

![](media/2022-10-22-13-36-51.png)

#### Business questions addressed and actions taken

### Data source

### Storage mode and data freshness

### Current usage

![](media/2022-10-22-13-36-13.png)

### Target users

### Security and data restrictions

### Value thresholds

### Business criticality (availability)

### Possible improvements

## Commerical Netback

Existing Commerical Netback report example

![](./media/existing-commercial-netback-report.png)

### Overview

The commercial netback is the revenue received for any given
transaction. Calculated in the payment terms.

#### Business questions addressed and actions taken

### Data source

### Related tables

### Storage mode

### Current usage

Monthly. Currently, the sales people pull the data into Excel.

### Target users

Sales

### Security and data restrictions

### Value thresholds

### Business criticality (availability)

### Possible improvements

## Environmental Unified

### Overview

#### Business questions addressed and actions taken

### Data source

### Storage mode and data freshness

### Current usage

### Target users

### Security and data restrictions

### Value thresholds

### Business criticality (availability)

### Possible improvements

## Commerical Netback

Existing Commerical Netback report example

![](./media/existing-commercial-netback-report.png)

### Overview

#### Business questions addressed and actions taken

### Data source

### Related tables

### Storage mode

### Current usage

The commerical sales team will analyze products and the customer and
measures in Excel based on the dataset.

### Target users

Commerical Sales

### Security and data restrictions

### Value thresholds

### Business criticality (availability)

### Possible improvements

## Off Spec

### Overview

![](media/2022-10-31-10-43-32.png) \#### Business questions addressed
and actions taken

### Data source

### Storage mode and data freshness

### Current usage

### Target users

### Security and data restrictions

### Value thresholds

### Business criticality (availability)

### Possible improvements

## P2-Data

### Overview

![](media/2022-10-31-11-09-54.png)

![](media/2022-10-31-11-10-12.png)

#### Business questions addressed and actions taken

### Data source

### Storage mode and data freshness

### Current usage

### Target users

### Security and data restrictions

### Value thresholds

### Business criticality (availability)

### Possible improvements

## Process (Unified)

### Overview

![](media/2022-10-31-11-52-31.png)

![](media/2022-10-31-11-52-52.png)

![](media/2022-10-31-11-53-10.png)

![](media/2022-10-31-11-53-25.png)

![](media/2022-10-31-11-53-42.png)

![](media/2022-10-31-11-53-59.png)

![](media/2022-10-31-11-54-16.png)

![](media/2022-10-31-11-54-37.png)

![](media/2022-10-31-11-55-00.png)

#### Business questions addressed and actions taken

### Data source

### Related tables

### Storage mode

### Current usage

### Target users

### Security and data restrictions

### Value thresholds

### Business criticality (availability)

### Possible improvements

## Quality (Unified) dataset

![](media/2022-11-02-15-46-01.png)

### Important facts

-   wsi_palletlot
-   wsi_productionorder \## Quality (Unified)

### Overview

![](media/2022-11-02-15-31-56.png)

#### Business questions addressed and actions taken

### Data source

### Related tables

![](media/2022-11-02-15-34-17.png)

### Storage mode

-   DirectQuery

### Current usage

### Target users

### Security and data restrictions

### Value thresholds

### Business criticality (availability)

### Possible improvements

## Release production orders

### Overview

![](media/2022-10-31-15-31-40.png)

#### Business questions addressed and actions taken

### Data source

### Related tables

### Storage mode

### Current usage

### Target users

### Security and data restrictions

### Value thresholds

### Business criticality (availability)

### Possible improvements

## High-Level P1 Ops Dashboard

## Type - Operational dashboard

![](./media/existing-high-level-p1-ops-dashboard.png)

![](media/2022-10-22-13-32-22.png)

## P1 Operational Dashboard

### Overview

### Type - Operational dashboard

![](media/2022-10-22-13-39-54.png)

### Usage metrics

![](media/2022-10-22-13-41-05.png)

### Target audience

### Actions taken

## Automation opportunities

## Existing workflows

-   Do you send reports to users via subscription or Microsoft Flow?
-   Do you have any scheduled batch data processing? What are the
    reporting needs?

## Workflow production

![](media/2022-10-31-11-07-01.png)

> Note: Confirm with client

## Tools

-   Power BI
    -   Datasets?
    -   Data Flows?
-   Excel
-   SSAS
-   SharePoint - available, not implemented in the organization.
-   OneDrive
-   Power Automate
    -   Flow
-   Common Data Source/Dataverse

## Development teams and roles

-   Steven Chambers
-   Eric Turner

## Version control

## Project management tools

-   MS Project?
-   Agile/Kanban?

## Change management and adoption

-   Gathering requirements
-   Reporting usage metrics gathering and review

## QA and Deployment process

### Deployment schedules and windows

## Data archiving

## Color scheme

## Desired processes

-   Allow users to build reports from validated data mart.
-   Reduce the need to pull from transactional systems.

![](media/2022-10-27-15-36-50.png)

## Color scheme

-   Reports should have a consistent look and feel.

## Development process

-   Deployment should be methodical after testing

-   Report development should not stress production workloads

-   Workspaces should be organized according to business units

    Example workspace names: Development Finance Sales Purchasing
    Production

## Workspace access

-   Manage working teams.
    -   Identify working teams.
    -   Set up Active Directory groups.
    -   Apply AD groups to Power BI workspaces.
