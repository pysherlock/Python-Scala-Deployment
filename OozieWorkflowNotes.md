# Oozie

  Oozie is a **server based Workflow Engine specialized in running workflow jobs with actions** that run Hadoop Map/Reduce, Spark, Shell Script and Pig jobs. Sceduling tools like crontab, but it could make the workflow according to both **time and file avalibility**. 
  
  Oozie v3 is a server based Bundle Engine that provides a higher-level oozie abstraction that will batch a set of coordinator applications. The user will be able to start/stop/suspend/resume/rerun a set coordinator jobs in the bundle level resulting a better and easy operational control.

## 1. Bundle, Coordinator & Workflow

  Bundle: bundle.xml + bundle.properties
  Includes a set of coordinators. All of them will use same parameters from bundle.properties except re-defination in coordinator
  Spec: 
  

  Coordinator: coordinator.xml + coordinator.properties (useless when it is started by bundle)
  Spec: https://oozie.apache.org/docs/3.1.3-incubating/CoordinatorFunctionalSpec.html#a6._Coordinator_Application
  
  Workflow: workflow.xml + job.properties 
  job.properties would be useless when it is triggered by coordinator (coordinator.properties), or a coordinator triggered by bundle (bundle.properties)
  Spec: https://oozie.apache.org/docs/4.0.1/WorkflowFunctionalSpec.html#a4_Parameterization_of_Workflows


