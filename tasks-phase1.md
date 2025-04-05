IMPORTANT ❗ ❗ ❗ Please remember to destroy all the resources after each work session. You can recreate infrastructure by creating new PR and merging it to master.

![img.png](doc/figures/destroy.png)

1. Authors:

   Group nr.: 8
   - Aleksander Świniarski (309423)
   - Marta Sobol (318723)
   - Magdalena Kalińska (310242)

   [Forked Repo](https://github.com/AleksanderSwiniarski/tbd-workshop-1)

2. Follow all steps in README.md.

3. In boostrap/variables.tf add your emails to variable "budget_channels".

4. From avaialble Github Actions select and run destroy on main branch.

5. Create new git branch and:
    1. Modify tasks-phase1.md file.

    2. Create PR from this branch to **YOUR** master and merge it to make new release.

    ![release.png](doc/figures/release.png)


6. Analyze terraform code. Play with terraform plan, terraform graph to investigate different modules.

    Graf modułu:
    ![img.png](modules/composer/graph.png)

    Opis:
    Moduł Composer odpowiada za automatyczne utworzenie środowiska Cloud Composer 2 (czyli zarządzanego Airflowa) w Google Cloud Platform. W ramach działania tworzy dedykowane konto serwisowe, przypisuje mu niezbędne role IAM (w tym composer.worker, dataproc.editor i serviceAccountUser) oraz aktywuje wymagane API. Dodatkowo tworzy podsieć w ramach wskazanej sieci VPC, którą następnie przekazuje do modułu Composer jako środowisko sieciowe. Środowisko jest konfigurowane z parametrami dotyczącymi zasobów (CPU, RAM, storage) dla schedulera, webserwera i workerów.


7. Reach YARN UI

   ***place the command you used for setting up the tunnel, the port and the screenshot of YARN UI here***

    Aby dostać się do konsoli YARN użyliśmy komendy:
    ``` bash
    gcloud compute ssh tbd-cluster-m \
    --project=tbd-2025l-9921 \
    --zone=europe-west1-d \
    -- -L 8088:localhost:8088
    ```
    A następnie w przeglądarce weszliśmy na adres : ```http://localhost:8088```

    ![hadoop.png](doc/figures/hadoop_yarn_ui.png)

8. Draw an architecture diagram (e.g. in draw.io) that includes:
    1. VPC topology with service assignment to subnets
    2. Description of the components of service accounts
    3. List of buckets for disposal
    4. Description of network communication (ports, why it is necessary to specify the host for the driver) of Apache Spark running from Vertex AI Workbech

    ***place your diagram here***

9. Create a new PR and add costs by entering the expected consumption into Infracost
For all the resources of type: `google_artifact_registry`, `google_storage_bucket`, `google_service_networking_connection`
create a sample usage profiles and add it to the Infracost task in CI/CD pipeline. Usage file [example](https://github.com/infracost/infracost/blob/master/infracost-usage-example.yml)

   ***place the expected consumption you entered here***

   ***place the screenshot from infracost output here***

10. Create a BigQuery dataset and an external table using SQL

    ***place the code and output here***

    ***why does ORC not require a table schema?***

11. Find and correct the error in spark-job.py

    ***describe the cause and how to find the error***

12. Add support for preemptible/spot instances in a Dataproc cluster

    ***place the link to the modified file and inserted terraform code***


