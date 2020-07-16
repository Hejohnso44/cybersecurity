---
 - name: Installing and Launch Filebeat
   hosts: webservers
   become: yes
   tasks:
   - name: Download filebeat .deb file
     command: curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.4.0-amd64.deb
   - name: Install filebeat .deb
     command: dpkg -i filebeat-7.4.0-amd64.deb
   - name: Drop in filebeat.yml
     copy:
       src: /etc/ansible/files/filebeat-config.yml
       dest: /etc/filebeat/filebeat.yml
   - name: Enable and Configure System Module
     command: filebeat modules enable system
   - name: Setup filebeat
     command: filebeat setup
   - name: Start filebeat service
     command: service filebeat start
   - name: Download metricbeat .deb file
     command: curl -L -O https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-7.4.0-amd64.deb
   - name: install .deb
     command: sudo dpkg -i metricbeat-7.4.0-amd64.deb
   - name: Drop in metricbeat
     copy:
       src: /etc/ansible/files/metricbeat-config.yml
       dest: /etc/metricbeat/metricbeat.yml
   - name: metricbeat modules enable system
     command: setup metricbeat
   - name: setup metricbeat
     command: metricbeat start
   - name: start metribeat
     command: service metricbeat start