# DevOps_Learning_24
Some Devops tasks

Yes! Instead of updating `README.md`, we can create a separate file named **`Dev_Read_me.md`** and push it to your repo.

---

### ✅ **Steps to Add `Dev_Read_me.md` to Git**

1. **Go to your project directory:**

```bash
cd ~/devops/week1-linux-cli/ansible-test
```

2. **Create the file:**

```bash
vi Dev_Read_me.md
```

3. **Paste the detailed document content** (I will provide it below).

4. **Save and commit it to Git:**

```bash
git add Dev_Read_me.md
git commit -m "Added Dev_Read_me.md with detailed Week 1 tasks"
git push origin main
```

---

### 📄 **Content for Dev\_Read\_me.md**

````markdown
# Week 1: Linux + CLI + Ansible Basics

We automated 3 key tasks using **Ansible**.

---

## ✅ Task 1: Ansible Ping Test
**Objective:** Verify Ansible connectivity to localhost.

### Steps:
1. Install Ansible:
   ```bash
   sudo apt update && sudo apt install ansible -y
````

2. Create inventory:

   ```
   [local]
   localhost ansible_connection=local
   ```
3. Create playbook:

   ```yaml
   ---
   - name: Test Ansible Ping
     hosts: local
     tasks:
       - name: Ping localhost
         ansible.builtin.ping:
   ```
4. Run:

   ```bash
   ansible-playbook -i inventory test-playbook.yml
   ```

---

## ✅ Task 2: Create Multiple Users

**Objective:** Automate Linux user creation.

### Playbook:

```yaml
---
- name: Create DevOps users
  hosts: local
  become: yes
  tasks:
    - name: Create devuser1
      ansible.builtin.user:
        name: devuser1
        state: present

    - name: Create devuser2
      ansible.builtin.user:
        name: devuser2
        state: present
```

Run:

```bash
sudo ansible-playbook -i inventory create-users.yml
```

Verify:

```bash
cat /etc/passwd | grep devuser
```

---

## ✅ Task 3: Host index.html on Apache

**Objective:** Automate Apache installation and serve a webpage.

### Playbook:

```yaml
---
- name: Host index.html on Apache Web Server
  hosts: local
  become: yes
  tasks:
    - name: Install Apache
      ansible.builtin.package:
        name: apache2
        state: present

    - name: Start Apache in WSL
      ansible.builtin.command: service apache2 start

    - name: Copy index.html
      ansible.builtin.copy:
        src: index.html
        dest: /var/www/html/index.html
        owner: www-data
        group: www-data
        mode: '0644'
```

Access:

* WSL: `curl http://localhost:8080`
* Browser: `http://localhost:8080`

---

## 🔗 GitHub Commands:

```bash
git add Dev_Read_me.md
git commit -m "Added Dev_Read_me.md with detailed Week 1 tasks"
git push origin main
```

```

---

Would you like me to **generate this file automatically using a single shell command**, so you don’t need to manually open the editor?
```
