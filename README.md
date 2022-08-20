# Ansible Role: Known Hosts

I have a [git repository](https://github.com/schuam/known_hosts.d) with public
ssh key which I believe to be correct. These keys belong to services that I use
regularly on different machines. In order to not have to check the keys every
time I use one of these services on a new machine, I set up this role. It
clones my git repo to /etc/ssh/known_hosts.d/ and then makes a linke
/etc/ssh/ssh_known_hosts that points to the ssh_known_hosts file in that repo.

This way, there are system-wide known hosts that are known to any user of the
system. Additionally each user can have their own addtional known hosts in
~/.ssh/known_hosts.


# Requirements

None


# Role Variables

The following variables can be found in vars/main.yml.

- known_hosts_repo_local_destination: Location to which the known host repo
                                      will be cloned.
- known_hosts_file_name:              Name of the system-wide known host file.
- known_hosts_link_path:              Path of the link to the known host file.

The following variables can be found in defaults/main.yml:

known_hosts_repo:             URL to the repo holding the public ssh keys.
known_hosts_repo_version:     Version of the repo to be cloned.
known_hosts_repo_remote_name: Name of the remote in the cloned repo.


# Dependencies

None


# Example Playbook

    - hosts: servers
      roles:
         - { role: schuam.known_hosts }


## License

MIT


## Author Information

This role was created in 2022 by [Andreas Schuster](https://www.schuam.de/).

