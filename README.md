# acit4640-wk4

## Instructions on general set up:

### Download Files:

<pre><font color="#26A269"><b>user@Debian13</b></font>:<font color="#12488B"><b>~/Downloads/week4</b></font>$ git clone https://gitlab.com/cit_4640/4640-w4-lab-start-w25
cd 4640-w4-lab-start-w25
Cloning into &apos;4640-w4-lab-start-w25&apos;...
</pre>

### Download and Install Terraform:

<pre>wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo &quot;deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(grep -oP &apos;(?&lt;=UBUNTU_CODENAME=).*&apos; /etc/os-release || lsb_release -cs) main&quot; | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update &amp;&amp; sudo apt install terraform
</pre>


# keygen:
<pre><font color="#26A269"><b>user@Debian13</b></font>:<font color="#12488B"><b>~/Downloads/week4/4640-w4-lab-start-w25</b></font>$ ssh-keygen -t ed25519 -C &quot;wk4&quot; -f ~/.ssh/wk4 -N &quot;&quot;
Generating public/private ed25519 key pair.
Your identification has been saved in /home/user/.ssh/wk4
</pre>

## NOTE: Add Public Key to cloud-config.yml in the ssh-authorized-keys sections

# Terraform and SSH Commands once everything was written:
<pre><font color="#26A269"><b>user@Debian13</b></font>:<font color="#12488B"><b>~/Downloads/week4/4640-w4-lab-start-w25</b></font>$ terraform init
</pre>
<pre><font color="#26A269"><b>user@Debian13</b></font>:<font color="#12488B"><b>~/Downloads/week4/4640-w4-lab-start-w25</b></font>$ terraform fmt -recursive
main.tf
<font color="#26A269"><b>user@Debian13</b></font>:<font color="#12488B"><b>~/Downloads/week4/4640-w4-lab-start-w25</b></font>$ terraform validate
<font color="#26A269"><b>Success!</b></font> The configuration is valid.

<font color="#26A269"><b>user@Debian13</b></font>:<font color="#12488B"><b>~/Downloads/week4/4640-w4-lab-start-w25</b></font>$ terraform plan -out tfplan
terraform apply &quot;tfplan&quot;
<b>data.aws_ami.debian: Reading...</b>
</pre>

<pre><font color="#26A269"><b>Apply complete! Resources: 11 added, 0 changed, 0 destroyed.</b></font>

<font color="#26A269"><b>Outputs:</b></font>

instance_ip_addr = {
  &quot;dns_name&quot; = &quot;ec2-34-220-33-96.us-west-2.compute.amazonaws.com&quot;
  &quot;public_ip&quot; = &quot;34.220.33.96&quot;
}
<font color="#26A269"><b>user@Debian13</b></font>:<font color="#12488B"><b>~/Downloads/week4/4640-w4-lab-start-w25</b></font>$ ssh -i ~/.ssh/wk4 web@ec2-34-220-33-96.us-west-2.compute.amazonaws.com
The authenticity of host &apos;ec2-34-220-33-96.us-west-2.compute.amazonaws.com (34.220.33.96)&apos; can&apos;t be established.
ED25519 key fingerprint is SHA256:HH90gyY1LzFMEw2SMA2r7bnQM8sn+3dM06GdLTwtW88.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added &apos;ec2-34-220-33-96.us-west-2.compute.amazonaws.com&apos; (ED25519) to the list of known hosts.
Linux ip-10-0-1-170 6.12.48+deb13-cloud-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.12.48-1 (2025-09-20) x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
<font color="#26A269"><b>web@ip-10-0-1-170</b></font>:<font color="#12488B"><b>~</b></font>$ 
</pre>

