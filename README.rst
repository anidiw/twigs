=====
twigs
=====


.. image:: https://img.shields.io/pypi/v/twigs.svg
        :target: https://pypi.python.org/pypi/twigs

.. image:: https://readthedocs.org/projects/twigs/badge/?version=latest
        :target: https://twigs.readthedocs.io/en/latest/?badge=latest
        :alt: Documentation Status




ThreatWatch Information Gathering Script

https://threatwatch.io/

* Free software: GNU General Public License v3
* Documentation: https://twigs.readthedocs.io.


Features
--------

twigs.py - A python script to discover various types of assets (cloud-based, Linux hosts, containers, repositories and more).

Note:
1. twigs supports python 2.7 onwards and python 3.x versions
2. It is recommended to use virtual environments to create isolated Python environments and reduce dependency conflicts. Please use the following commands to create new virtual environment and install twigs:

Python 2.7 Virtual Environment:

python -m virtualenv --python=/usr/bin/python2.7 twigs_env_2_7

cd twigs_env_2_7

source bin/activate

pip install twigs


Python 3.x Virtual Environment:

python3 -m venv twigs_env

cd twigs_env

source bin/activate

pip3 install twigs


$ twigs --help
usage: twigs [-h] [--version] [--handle HANDLE] [--token TOKEN] [--instance INSTANCE] [--tag_critical] [--tag TAG] [--apply_policy APPLY_POLICY] [--out OUT] [--no_scan] [--email_report] [-q | -v] [--schedule SCHEDULE] [--encoding ENCODING] {aws,azure,acr,gcp,gcr,docker,host,nmap,repo,file,servicenow,docker_cis,aws_cis,azure_cis,gcp_cis,ssl_audit,dast}

ThreatWatch Information Gathering Script (twigs) to discover assets like hosts, cloud instances, containers and opensource projects

optional arguments:
  -h, --help            show this help message and exit
  --version         show program's version number and exit
  --handle HANDLE       The ThreatWatch registered email id/handle of the
                        user. Note this can set as "TW_HANDLE" environment
                        variable
  --token TOKEN         The ThreatWatch API token of the user. Note this can
                        be set as "TW_TOKEN" environment variable
  --instance INSTANCE   The ThreatWatch instance. Note this can be set as 
                        "TW_INSTANCE" environment variable
  --tag_critical        Tag the discovered asset(s) as critical
  --tag TAG             Add specified tag to discovered asset(s). You can
                        specify this option multiple times to add multiple
                        tags
  --apply_policy APPLY_POLICY
                        One or more policy names as a comma-separated list
  --out OUT             Specify name of the JSON file to hold the exported
                        asset information.
  --no_scan             Do not initiate a baseline assessment
  --email_report        After impact refresh is complete email scan report to
                        self
  --quiet               Disable verbose logging
  -v, --verbosity       Specify the verbosity level. Use multiple times to
                        increase verbosity level
  --schedule SCHEDULE   Run this twigs command at specified schedule (crontab format)
  --encoding ENCODING   Specify the encoding. Default is "latin-1"

modes:
  Discovery modes supported

{login,logout,aws,azure,acr,gcp,gcr,docker,host,nmap,repo,file,servicenow,docker_cis,aws_cis,azure_cis,gcp_cis,ssl_audit,dast}
    login               Login to twigs
    logout              Logout from twigs
    aws                 Discover AWS instances
    azure               Discover Azure instances
    acr                 Discover Azure Container Registry (ACR) container images
    gcp                 Discover Google Cloud Platform (GCP) instances
    gcr                 Discover Google Cloud Registry (GCR) container images
    docker              Discover docker instances
    file                Discover inventory from file
    host                Discover linux host assets
    nmap                Fingerprint assets using nmap. Requires nmap to be installed.
    repo                Discover project repository as asset
    servicenow          Discover inventory from ServiceNow instance
    docker_cis          Run docker CIS benchmarks
    aws_cis             Run AWS CIS benchmarks
    azure_cis           Run Azure CIS benchmarks
    gcp_cis             Run Google Cloud Platform CIS benchmarks
    ssl_audit           Run SSL audit tests against your web URLs. Requires [twigs_ssl_audit] package to be installed
    dast                Discover and test web application using a DAST plugin

Mode: login
usage: twigs login [-h]

optional arguments:
  -h, --help  show this help message and exit

Mode: logout
usage: twigs logout [-h]

optional arguments:
  -h, --help  show this help message and exit

Mode: aws
$ twigs aws --help
usage: twigs aws [-h] --aws_account AWS_ACCOUNT --aws_access_key AWS_ACCESS_KEY --aws_secret_key AWS_SECRET_KEY --aws_region AWS_REGION --aws_s3_bucket AWS_S3_BUCKET [--enable_tracking_tags]

optional arguments:
  -h, --help            show this help message and exit
  --aws_account AWS_ACCOUNT
                        AWS account ID
  --aws_access_key AWS_ACCESS_KEY
                        AWS access key
  --aws_secret_key AWS_SECRET_KEY
                        AWS secret key
  --aws_region AWS_REGION
                        AWS region
  --aws_s3_bucket AWS_S3_BUCKET
                        AWS S3 inventory bucket
  --enable_tracking_tags
                        Enable recording AWS specific information (like AWS
                        Account ID, etc.) as asset tags

Help video: https://youtu.be/pYzHU7izRdU

Mode: azure
$ twigs azure --help
usage: twigs azure [-h]  --azure_tenant_id AZURE_TENANT_ID --azure_application_id AZURE_APPLICATION_ID --azure_application_key AZURE_APPLICATION_KEY [--azure_subscription AZURE_SUBSCRIPTION] [--azure_resource_group AZURE_RESOURCE_GROUP] [--azure_workspace AZURE_WORKSPACE] [--enable_tracking_tags]

optional arguments:
  -h, --help            show this help message and exit
  --azure_tenant_id AZURE_TENANT_ID
                        Azure Tenant ID
  --azure_application_id AZURE_APPLICATION_ID
                        Azure Application ID
  --azure_application_key AZURE_APPLICATION_KEY
                        Azure Application Key
  --azure_subscription AZURE_SUBSCRIPTION
                        Azure Subscription. If not specified, then available
                        values will be displayed
  --azure_resource_group AZURE_RESOURCE_GROUP
                        Azure Resource Group. If not specified, then available
                        values will be displayed
  --azure_workspace AZURE_WORKSPACE
                        Azure Workspace. If not specified, then available
                        values will be displayed
  --enable_tracking_tags
                        Enable recording Azure specific information (like
                        Azure Tenant ID, etc.) as asset tags

Help video: https://youtu.be/DyMrxYscADw

Mode: acr
$ twigs acr --help
usage: twigs.py acr [-h] [--registry REGISTRY] [--image IMAGE] [--tmp_dir TMP_DIR]

optional arguments:
  -h, --help           show this help message and exit
  --registry REGISTRY  The Azure Container Registry which needs to be
                       inspected.
  --image IMAGE        The fully qualified image name (with tag) which needs
                       to be inspected. If tag is not given, latest will be
                       determined and used.
  --tmp_dir TMP_DIR    Temporary directory. Defaults to /tmp

Mode: gcp
$ twigs gcp --help
usage: twigs gcp [-h] [--enable_tracking_tags]

optional arguments:
  -h, --help            show this help message and exit
  --enable_tracking_tags
                        Enable recording GCP specific information (like
                        Project ID, etc.) as asset tags

Help video: https://youtu.be/tGgKZcGFfZ4

Mode: gcr
$ twigs gcr --help
usage: twigs gcr [-h] [--repository REPOSITORY] [--image IMAGE] [--tmp_dir TMP_DIR]

optional arguments:
  -h, --help            show this help message and exit
  --repository REPOSITORY
                        The GCR image respository url which needs to be
                        inspected.
  --image IMAGE         The fully qualified image name (with tag / digest)
                        which needs to be inspected. If tag / digest is not
                        given, latest will be determined and used.
  --tmp_dir TMP_DIR     Temporary directory. Defaults to /tmp

Mode: docker
$ twigs docker --help
usage: twigs docker [-h] [--image IMAGE] [--containerid CONTAINERID] [--assetid ASSETID] [--assetname ASSETNAME] [--tmp_dir TMP_DIR] [--start_instance]

optional arguments:
  -h, --help            show this help message and exit
  --image IMAGE         The docker image (repo:tag) which needs to be
                        inspected. If tag is not given, "latest" will be
                        assumed.
  --containerid CONTAINERID
                        The container ID of a running docker container which
                        needs to be inspected.
  --assetid ASSETID     A unique ID to be assigned to the discovered asset
  --assetname ASSETNAME
                        A name/label to be assigned to the discovered asset
  --tmp_dir TMP_DIR     Temporary directory to discover container
  --start_instance      If image inventory fails, try starting a container
                        instance to inventory contents. Use with caution

Mode: file
$ twigs file --help
usage: twigs file [-h] --input INPUT [--assetid ASSETID] [--assetname ASSETNAME] [--type {OpenSource}]

optional arguments:
  -h, --help            show this help message and exit
  --input INPUT         Absolute path to single input inventory file or a
                        directory containing JSON or CSV files. Supported file
                        formats are: CSV, JSON & PDF
  --assetid ASSETID     A unique ID to be assigned to the discovered asset.
                        Defaults to input filename if not specified. Applies
                        only for PDF files.
  --assetname ASSETNAME
                        A name/label to be assigned to the discovered asset.
                        Defaults to assetid is not specified. Applies only for
                        PDF files.
  --type TYPE           Type of asset. Defaults to repo if not specified.
                        Applies only for PDF files.

Mode: host
$ twigs host --help
usage: twigs host [-h] [--remote_hosts_csv REMOTE_HOSTS_CSV] [--host_list HOST_LIST] [--secure] [--password PASSWORD] [--assetid ASSETID] [--assetname ASSETNAME] [--no_ssh_audit] [--no_host_benchmark]

optional arguments:
  -h, --help            show this help message and exit
  --remote_hosts_csv REMOTE_HOSTS_CSV
                        CSV file containing details of remote hosts. CSV file
                        column header [1st row] should be: hostname,userlogin,
                        userpwd,privatekey,assetid,assetname. Note "hostname"
                        column can contain hostname, IP address, CIDR range.
  --host_list HOST_LIST
                        Same as the option: remote_hosts_csv. A file
                        (currently in CSV format) containing details of remote
                        hosts. CSV file column header [1st row] should be: hos
                        tname,userlogin,userpwd,privatekey,assetid,assetname.
                        Note "hostname" column can contain hostname, IP
                        address, CIDR range.
  --secure              Use this option to encrypt clear text passwords in the
                        host list file
  --password PASSWORD   A password use to encrypt / decrypt login information
                        from the host list file
  --assetid ASSETID     A unique ID to be assigned to the discovered asset
  --assetname ASSETNAME
                        A name/label to be assigned to the discovered asset
  --no_ssh_audit        Skip ssh audit
  --no_host_benchmark   Skip host benchmark audit

Help video: https://youtu.be/OKJ-DxXwanA

Mode: nmap
$ twigs nmap --help
usage: twigs nmap [-h] --hosts HOSTS

optional arguments:
  -h, --help     show this help message and exit
  --hosts HOSTS  A hostname, IP address or CIDR range
  --no_ssh_audit  Skip ssh audit

Mode: repo
$ twigs repo --help
usage: twigs repo [-h] --repo REPO [--type {pip,ruby,yarn,nuget,npm,maven,gradle,dll,jar,cargo}] [--level {shallow,deep}] [--assetid ASSETID] [--assetname ASSETNAME] [--secrets_scan] [--enable_entropy] [--regex_rules_file REGEX_RULES_FILE] [--check_common_passwords] [--common_passwords_file COMMON_PASSWORDS_FILE] [--include_patterns INCLUDE_PATTERNS] [--include_patterns_file INCLUDE_PATTERNS_FILE] [--exclude_patterns EXCLUDE_PATTERNS] [--exclude_patterns_file EXCLUDE_PATTERNS_FILE] [--mask_secret] [--no_code] [--sast]

optional arguments:
  -h, --help            show this help message and exit
  --repo REPO           Local path or git repo url for project
  --type TYPE           Type of open source component to scan for {pip,ruby,yarn,nuget,npm,maven,gradle,dll,jar,cargo}. Defaults to all supported types if not specified
  --level LEVEL         Possible values {shallow, deep}. Shallow restricts discovery to 1st level dependencies only. Deep discovers dependencies at all levels. Defaults to shallow discovery if not specified
  --assetid ASSETID     A unique ID to be assigned to the discovered asset
  --assetname ASSETNAME
                        A name/label to be assigned to the discovered asset
  --secrets_scan        Perform a scan to look for secrets in the code
  --enable_entropy      Identify entropy based secrets
  --regex_rules_file REGEX_RULES_FILE
                        Path to JSON file specifying regex rules
  --check_common_passwords
                        Look for top common passwords.
  --common_passwords_file COMMON_PASSWORDS_FILE
                        Specify your own common passwords file. One password per line in file
  --include_patterns INCLUDE_PATTERNS
                        Specify patterns which indicate files to be included in the secrets scan. Separate multiple patterns with comma.
  --include_patterns_file INCLUDE_PATTERNS_FILE
                        Specify file containing include patterns which indicate files to be included in the secrets scan. One pattern per line in file.
  --exclude_patterns EXCLUDE_PATTERNS
                        Specify patterns which indicate files to be excluded in the secrets scan. Separate multiple patterns with comma.
  --exclude_patterns_file EXCLUDE_PATTERNS_FILE
                        Specify file containing exclude patterns which indicate files to be excluded in the secrets scan. One pattern per line in file.
  --mask_secret         Mask identified secret before storing for reference in ThreatWatch.
  --no_code             Disable storing code for reference in ThreatWatch.
  --sast                Perform static code analysis on your source code

Mode: servicenow
$ twigs servicenow --help
usage: twigs servicenow [-h] --snow_user SNOW_USER --snow_user_pwd SNOW_USER_PWD --snow_instance SNOW_INSTANCE [--enable_tracking_tags]

optional arguments:
  -h, --help            show this help message and exit
  --snow_user SNOW_USER
                        User name of ServiceNow account
  --snow_user_pwd SNOW_USER_PWD
                        User password of ServiceNow account
  --snow_instance SNOW_INSTANCE
                        ServiceNow Instance name
  --enable_tracking_tags
                        Enable recording ServiceNow specific information (like
                        ServiceNow instance name, etc.) as asset tags

Mode: docker_cis
$ twigs docker_cis --help
usage: twigs docker_cis [-h] [--assetid ASSETID] [--assetname ASSETNAME] [--docker_bench_home DOCKER_BENCH_HOME]

optional arguments:
  -h, --help            show this help message and exit
  --assetid ASSETID     A unique ID to be assigned to the discovered asset
  --assetname ASSETNAME
                        A name/label to be assigned to the discovered asset
  --docker_bench_home DOCKER_BENCH_HOME
                        Location of docker bench CLI

Mode: aws_cis
$ twigs aws_cis --help
usage: twigs aws_cis [-h] --aws_access_key AWS_ACCESS_KEY --aws_secret_key AWS_SECRET_KEY --assetid ASSETID [--assetname ASSETNAME] [--prowler_home PROWLER_HOME]

optional arguments:
  -h, --help            show this help message and exit
  --aws_access_key AWS_ACCESS_KEY
                        AWS access key
  --aws_secret_key AWS_SECRET_KEY
                        AWS secret key
  --assetid ASSETID     A unique ID to be assigned to the discovered asset
  --assetname ASSETNAME
                        A name/label to be assigned to the discovered asset
  --prowler_home PROWLER_HOME
                        Location of cloned prowler github repo. Defaults to
                        current directory

Mode: azure_cis
$ twigs azure_cis --help
usage: twigs azure_cis [-h] --assetid ASSETID [--assetname ASSETNAME]

optional arguments:
  -h, --help            show this help message and exit
  --assetid ASSETID     A unique ID to be assigned to the discovered asset
  --assetname ASSETNAME
                        A name/label to be assigned to the discovered asset

Mode: gcp_cis
$ twigs gcp_cis --help
usage: twigs gcp_cis [-h] --assetid ASSETID [--assetname ASSETNAME]

optional arguments:
  -h, --help            show this help message and exit
  --assetid ASSETID     A unique ID to be assigned to the discovered asset
  --assetname ASSETNAME
                        A name/label to be assigned to the discovered asset

Mode: ssl_audit
$ twigs ssl_audit --help
usage: twigs ssl_audit [-h] --url URL [--args ARGS] [--info] --assetid ASSETID [--assetname ASSETNAME]

optional arguments:
  -h, --help            show this help message and exit
  --url URL             HTTPS URL
  --args ARGS           Optional extra arguments
  --info                Report LOW / INFO level issues
  --assetid ASSETID     A unique ID to be assigned to the discovered web URL
                        asset
  --assetname ASSETNAME
                        Optional name/label to be assigned to the web URL
                        asset

Mode: dast
$ twigs dast --help
usage: twigs dast [-h] --url URL [--plugin {arachni,skipfish}] [--pluginpath PLUGINPATH] [--args ARGS] --assetid ASSETID [--assetname ASSETNAME]

optional arguments:
  -h, --help            show this help message and exit
  --url URL             Web application URL
  --plugin PLUGIN       DAST plugin to be used. Default is arachni. Requires
                        the plugin to be installed separately.
  --pluginpath PLUGINPATH
                        Path where the DAST plugin is installed to be used.
                        Default is /usr/bin.
  --args ARGS           Optional extra arguments to be passed to the plugin
  --assetid ASSETID     A unique ID to be assigned to the discovered webapp
                        asset
  --assetname ASSETNAME
                        Optional name/label to be assigned to the webapp asset

Note: For Windows hosts, you can use provided PowerShell script (twigs.ps1) for discovery. It requires PowerShell 3.0 or higher.

usage: .\\twigs.ps1 -?

twigs.ps1 [-handle] <String> [[-token] <String>] [[-instance] <String>] [[-out] <String>] [[-assetid] <String>] [[-assetname] <String>] [-tag_critical] [[-tags] <String[]>] [<CommonParameters>]

Credits
-------

This package was created with Cookiecutter_ and the `audreyr/cookiecutter-pypackage`_ project template.

.. _Cookiecutter: https://github.com/audreyr/cookiecutter
.. _`audreyr/cookiecutter-pypackage`: https://github.com/audreyr/cookiecutter-pypackage
