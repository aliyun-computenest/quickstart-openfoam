<h1> Rapid deployment OpenFOAM Ehpc compute nest </h1>

<blockquote>
<p><strong> Disclaimer:</strong> This service is provided by a third party. We try our best to ensure its security, accuracy and reliability, but we cannot guarantee that it is completely free from failure, interruption, error or attack. Therefore, the company hereby declares that it makes no representations, warranties or commitments regarding the content, accuracy, completeness, reliability, suitability and timeliness of the Service and is not liable for any direct or indirect loss or damage arising from your use of the Service; for third-party websites, applications, products and services that you access through the Service, do not assume any responsibility for its content, accuracy, completeness, reliability, applicability and timeliness, and you shall bear the risks and responsibilities of the consequences of use; for any loss or damage arising from your use of this service, including but not limited to direct loss, indirect loss, loss of profits, loss of goodwill, loss of data or other economic losses, even if we have been advised in advance of the possibility of such loss or damage; we reserve the right to amend this statement from time to time, so please check this statement regularly before using the Service. If you have any questions or concerns about this Statement or the Service, please contact us. </p>
</blockquote>

<h2> Overview </h2>

<p>OpenFOAM(Open Source Field Operation and Manipulation) is a software for numerical calculation of continuous medium mechanics problems. Data pre-processing, post-processing, and custom solvers are available for use in computational fluid dynamics. For more information, please see OpenFOAM official website. </p>

<h2> Prerequisites </h2>

<p> To deploy OpenFOAM community edition service instances, you need to access and create some Alibaba Cloud resources. Therefore, your account must contain permissions for the following resources.
<strong> Note </strong>: This permission is required only when your account is a RAM account. </p>

<table>
<thead>
<tr>
<th> Permission policy name </th>
<th> Remarks </th>
</tr>
</thead>
<tbody>
<tr>
<td>AliyunECSFullAccess</td>
<td> Permissions to manage ECS </td>
</tr>
<tr>
<td>AliyunVPCFullAccess</td>
<td> Permissions for managing VPC networks </td>
</tr>
<tr>
<td>AliyunROSFullAccess</td>
<td> Manage permissions for Resource Orchestration Services (ROS) </td>
</tr>
<tr>
<td>AliyunEHPCFullAccess</td>
<td> Permissions to manage Elastic High Performance Computing (EHPC) </td>
</tr>
<tr>
<td>AliyunNASFullAccess</td>
<td> Manage NAS permissions </td>
</tr>
<tr>
<td>AliyunComputeNestUserFullAccess</td>
<td> Manage user-side permissions for the compute nest service (ComputeNest) </td>
</tr>
</tbody>
</table>

<h2> Billing instructions </h2>

<p> the cost of OpenFOAM community edition deployment in computing nest mainly involves:</p>

<ul>
<li> Elastic High Performance Computing Cluster (EHPC) fees </li>
<li> File System (NAS) fees </li>
<li> Traffic bandwidth charges </li>
</ul>

<h2> Deployment Architecture </h2>

<p><img src="1.png" width="1500" height="700" align="bottom"/></p>

<ul>
<li> The deployment consists of an ehpc cluster, which includes manager nodes, schedule nodes, and compute nodes. </li>
<li> The service uses nas-cpfs to build a high-performance shared file system </li>
</ul>

<h2> Parameter description </h2>

<table>
<thead>
<tr>
<th> Parameter group </th>
<th> Parameter item </th>
<th> Description </th>
</tr>
</thead>
<tbody>
<tr>
<td> Service instance </td>
<td> Service instance name </td>
<td> It must be no more than 64 characters in length and must start with an English letter. It can contain numbers, English letters, dashes (-), and underscores (_). </td>
</tr>
<tr>
<td></td>
<td> Region </td>
<td> Region where the service instance is deployed </td>
</tr>
<tr>
<td></td>
<td> Payment type </td>
<td> Resource billing type: Pay-As-You-Go and Subscription </td>
</tr>
<tr>
<td>EHPC cluster configuration </td>
<td> Cluster logon password </td>
<td> is 8-30 in length and must contain three items (uppercase letters, lowercase letters, numbers, ()'~!@#$%^& *-+ =|{}[]:' <>,./special symbols)</td>
</tr>
<tr>
<td></td>
<td>Ehpc deployment mode </td>
<td>Tiny,Simple,Standard</td>
</tr>
<tr>
<td></td>
<td> Compute node instance type </td>
<td> Specifications of compute nodes available in the zone </td>
</tr>
<tr>
<td></td>
<td> Calculate the number of nodes </td>
<td> Number of computing nodes, optional value: 1-99</td>
</tr>
<tr>
<td></td>
<td> Login node instance type </td>
<td> Specifications of logon nodes available in the zone </td>
</tr>
<tr>
<td></td>
<td> Number of control nodes </td>
<td> Number of control nodes, optional values: 1,2,4</td>
</tr>
<tr>
<td>EHPC cluster user configuration </td>
<td> User password </td>
<td> is 8-30 in length and must contain three items (uppercase letters, lowercase letters, numbers, ()~!@#$%^& *-_+ ={}[]:; Special symbols in '/<>,.?/)</td>
</tr>
<tr>
<td></td>
<td> User Name </td>
<td> The user name used to log on to the cluster. Default value: foamtest</td>
</tr>
<tr>
<td> Network configuration </td>
<td> Availability Zone </td>
<td> Zone where the ECS instance is located </td>
</tr>
<tr>
<td></td>
<td>VPC ID</td>
<td> VPC where the resource is located </td>
</tr>
<tr>
<td></td>
<td> Switch ID</td>
<td> Switch where the resource is located </td>
</tr>
</tbody>
</table>

<h2> Deployment process </h2>

<ol>
<li><p> Visit the computing nest OpenFOAM community version <a href = "https://computenest.console.aliyun.com/service/instance/create/cn-hangzhou?type=user&ServiceId=service-9b427cbf0dcf4d5b988d"> deployment link </a> and fill in the deployment parameters as prompted:
<img src="2.png" alt="image.png" /></p></li>
<li><p> after the parameters are filled in, you can see the corresponding inquiry details. after confirming the parameters, click <strong> next: confirm the order </strong>.
<img src="3.png" alt="image.png" /></p></li>
<li><p> Confirm the order and agree to the service agreement and click <strong> Create now </strong>
Enter the deployment phase.
<img src="4.png" alt="image.png" /></p></li>
</ol>

<h2> Using Process </h2>

<h3> Step 1: Connect to the cluster through the console </h3>

<ol>
<li> Log on to the <a href = "https://ehpc.console.aliyun.com"> Elastic HPC console </a>. </li>
<li> In the top-left corner of the menu bar, select a region. </li>
<li> In the left-side navigation pane, click <strong> Clusters </strong>. </li>
<li> On the <strong> Clusters </strong> page, find the target cluster deployed in the computing nest and click <strong> Remote Connection </strong>.
<img src="5.png" height="700" align="bottom"/></li>
<li> On the <strong> Remote Connection </strong> page, enter the cluster username, logon password, and port number, and click <strong> SSH Connection </strong>. </li>
</ol>

<h3><strong> Step 2: Run the example </strong></h3>

<p> In this paper, the motorcycle outflow field is calculated using the simpleFoam solver in the OpenFOAM, and the study path is $FOAM_TUTORIALS/incompressible/simpleFoam/motorBike/. </p>

<p>1. Set environment variables. </p>

<pre><code>export MODULEPATH=/opt/ehpcmodulefiles/
module load openfoam-openmpi/5.0
module load openmpi/1.10.7
</code></pre>

<p>2. Prepare the study file. </p>

<pre><code>mkdir /home/foamtest/motorBike
cp -r /opt/OpenFOAM/OpenFOAM-5.0/tutorials/incompressible/simpleFoam/motorBike/* /home/foamtest/motorBike
</code></pre>

<p>3. Run the example. </p>

<pre><code>cd /home/foamtest/motorBike
source /opt/OpenFOAM/OpenFOAM-5.0/etc/bashrc
./Allrun
</code></pre>

<h3><strong> Step 3: View Results </strong></h3>

<p> Execute the following command to view the result file. </p>

<pre><code>cat /home/foamtest/motorBike/log.blockMesh
</code></pre>

<p> The expected return is as follows:
<img src="6.png" height="800" align="bottom"/></p>
