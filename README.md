# What is this repository?
This is an example repo containing Configuration as Code information for an Ansible Automation Platform (AAP) organization, using the method described [here](https://www.redhat.com/en/blog/creating-ansible-controller-config-code-pipeline). The organization defined in this example repo is named **org01**.

# What else is needed to use this repository?

The following are pre-requisites to use this repository[^1]:

- a generic **controller_automator** project needs to exist in AAP, as described in the above mentioned page. For an example repository that can be used to setup a **controller_automator** in AAP, see [https://github.com/aemelius/aap_central_automation.git].
- a set of AAP objects, specifically created for **org01** also need to exist in AAP:
  1.  a dedicated project for the organization **org01** needs to exist in AAP, pointing to this repo. Recommended name: **org01_cac**
  1. An inventory object (recommended name, for consistency: **org01_inv**)
  1. An inventory source object (recommended name: **org01_is**), associated with **org01_inv** and pointing to the **org01_cac** project
  1. A job template (recommended name: **org01_cac**), linking inventory **org01_inv** and project **controller_automator**
  1. a user named **org01_admin**, with administration privileges on the organization **org01** (privileges can be assigned via creating a dedicated **admin** role for the org)
  1. AAP credential of type **Red Hat Ansible Automation Platform**; depending on the version of the collection infra.aap_configuration being used, some variable mapping might be required to use the available env injectors for this type of credentials. For further details see the AAP documentation[^2] and the infra.aap_configuration collection documentation[^3].

The creation of the pre-requisite objects in AAP is *not* covered by this repository: they need to be either created manually, or via ansible cli using something like [https://gist.github.com/Tompage1994/cab31a119dfc1c9122ba202fe04c1978], keeping in mind that this gist covers the creation of CaC for an organization named "Default".



[^1]: https://www.redhat.com/en/blog/creating-ansible-controller-config-code-pipeline
[^2]: https://docs.redhat.com/en/documentation/red_hat_ansible_automation_platform/2.4/html-single/automation_controller_user_guide/index#ref-controller-credential-aap
[^3]: https://galaxy.ansible.com/ui/repo/published/infra/aap_configuration