k8s_users
=========

This role create roles and cluster roles.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should
be mentioned here. For instance, if the role uses the EC2 module, it may be a
good idea to mention in this section that the boto package is required.

Role Variables
--------------
Cluster roles:

```yaml
k8s_rbac_cluster_role:
  - name: test-cluster-role
    user: cluster-role-user
    namespace: default
    action: create
    api_groups:
      - name:
          - ""
          - "extensions"
          - "apps"
        resources:
          - "*"
        verbs:
          - "*"
```

Roles:
```yaml
k8s_rbac_role:
  - name: test-role
    namespace: testing
    user: test-r
    action: create
    api_groups:
      - name:
          - ""
          - "extensions"
          - "apps"
        resources:
          - "pods"
          - "pods/log"
        verbs:
          - "*"
```

- k8s_rbac_role: si esta presente creara Roles.
- k8s_rbac_cluster_role: si esta presente creara Cluster Roles.

- name: nombre de un Role o Cluster Role
- namespace: 
  - Namespace para el cual tendra alcance el Role.
  - Namespace donde se creara el Service Account, tanto para el Rol como para ClusterRol.
- user: nombre con el cual se creara el ServiceAccount.
- api_groups: en esta variable se especfican los permisos para cada Rol y ClusterRol.
  - name: nombre de cada api_group.
  - resources: listado de recursos a los cuales se asignaran permisos. Para asignar a todos: "*".
  - verbs: permisos asignados  a cada uno de los recursos. Para asignar a todos. "*"
- action: con esta variable vamos a indicar si se creara o eliminara un Role o ClusterRole.
  * Valores posibles: **create o delete**.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in
regards to parameters that may need to be set for other roles, or variables that
are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables
passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: geroafonso.k8s_users, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a
website (HTML is not allowed).
