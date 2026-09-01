# SupportTicketPlatform
Most companies run into many support/IT tickets but have no visibility into which ones are about to breach SLA (Service Level Agreement), and rely on manual input. This system solves this problem many companies face.

My Planned architecure goes as: 
1. Python script takes raw ticket exports in cloud storage (scheduled via Airflow)
2. Transform the data with dbt models
3. Use scikit-learn model to predict ticket priority and SLA-breach rish from text and metadata. 
4. Use LangGraph agent that classifies incoming tickets, retrieves similar resolved tickets and dradts a suggested resolution. 
5. Have LLM as a judge to score agent's classification against a labeled holdout set
6. Next.js + Prisma dashboard where agents see tickets, AI suggestions, and can override/approve
7. Power BI or Tableau exec dashboard on top of the warehouse marts
8. Plan to CI/CD & Deploy via Vercel and Docker