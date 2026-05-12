# 🔐 AWS Practical — SSH Key Authentication on Ubuntu EC2

> **Aim:** Create a custom Linux user on an AWS Ubuntu EC2 instance and allow secure SSH login using a generated SSH key pair.

---

## 📚 Table of Contents

1. Overview
2. Prerequisites
3. Generate SSH Key Pair
4. Launch Ubuntu EC2 Instance
5. Connect to EC2 Instance
6. Transfer Public Key to Server
7. Verify File on Server
8. Login Using Custom User & SSH Key
9. Commands Used
10. Conclusion

---

# 🧭 Overview

In this practical, we will:

* Generate an SSH key pair on Windows
* Launch an Ubuntu EC2 instance on AWS
* Copy the public key to the server
* Authenticate securely using SSH keys
* Login to the server without passwords

---

# ✅ Prerequisites

| Requirement  | Details                     |
| ------------ | --------------------------- |
| AWS Account  | Active AWS account          |
| EC2 Instance | Ubuntu Linux                |
| Terminal     | CMD / PowerShell / Git Bash |
| Key Pair     | AWS `.pem` file             |
| Internet     | Public IP access enabled    |

---

# 🚀 Step 1 — Generate SSH Key Pair on Windows

Move to the Downloads directory:

```bash
cd Downloads
```

Generate SSH key pair:

```bash
ssh-keygen
```

When prompted:

```text
Enter file in which to save the key: john
```

After successful execution:

```text
john       ← Private Key
john.pub   ← Public Key
```

---

## 📸 SSH Key Generation

![Image](https://images.openai.com/static-rsc-4/ek7wavaFbGTTosWT-0TFoW1ibAJXo9xtLN6q57nRlrAmGnzHAsChjKxhnuYqiAOagBcGUKV8KRPbUWAGh3XOxWML0wehaCGJ_3UsXE_fHzzLaBSFNpTGI-_rkaRle2aUg_ZKITTLkSGBEO9KR1dKWPZcZZarrE9xJqbfrvZB9Pc0nKvOhUrHepC36hbTO4JR?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/xUqEAUdtE4M8N3tV-C1z8Hip3QI6_8W3grwcoNMXTjXN3PLOWBq02id3V36vxiMN9aAaYswPKc7P3r654NAN6A6tWYC18DAL33wMv3HlqCrHsLdM1cToorATVtj_NM7YK8FCmb2ExeHtNYMNjgFYUl2dO4pWSbYwByl0cuOg0cUxXZDwo34r88Nwubk1Ueh7?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/RGT_FBLMshbClXVGUJAYWsZOKWsiPTHJBPV_JrGXuv-b0C8vQnL_XAOEfpwJAL73iHPJM6f1Ak8ko9EHNM-OxfwStv1BY_1lOn07ormf3PGgicHwLueyPrhAVYmSkoAlm0MVkNe8CsAl19MnzdyniLV4cEpCrxNr1UnVDfexRVm9XWgeM7Awzp_RJARpGIP4?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/CD8fj_L0_AUpCgraoxrgMWqX4G4Z-Q9LbLlXZsunlV9V5uxHbQ-ErHwIK1wyqi7JK_-i_ECtijwqeiNnbvcEBw8fWr7x6UTIP-1Oig1sY7bVuylTnX-ZJVNpJMeknxIFoU1OzLOfQ_9xNPJaSNWlkH2rI3XFLVg7een38_wA2fIjCUluURteQvdcevGosjPP?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/xzpZa5o24ptk2DKQOxuhUF0bU-P1czxk7AnQciZJmV9egj9fWnkojtqZR4XBETxmUeV6O_qVrv6CWg9oYaeAd0M2S-cVxOFr6kVyFxjUGYpfUWWWDC5YfmvJoEmp-zZniAKrjl7biZKtxLlwsNmX6FH7eJ6z9ev7dLu2p84qgy4JumVn1XgQ3QpCIYCJESUf?purpose=fullsize)

---

# ☁️ Step 2 — Launch Ubuntu EC2 Instance

1. Open AWS Console
2. Go to EC2 Dashboard
3. Launch Ubuntu Instance
4. Choose instance type (`t3.micro`)
5. Allow SSH (Port 22) in Security Group
6. Launch instance with AWS `.pem` key

---

## 📸 AWS EC2 Instance

![Image](https://images.openai.com/static-rsc-4/f8dNN7a5CNeogtQnwvGc7zLLC3AktGBsjlqUe5zmrCZ-S8xb5tA7d9HKDcIl2CEn1GI7KWxDnZhUKQpc6dSweGiavZfP0lr0MvW5vifNYuGF_4RGs_GDQI8BhR9E7r9nCmdVggfk0m9DYM7Y3y4gPzMADcdZaD_Car1PlFV5mpTyDDVEE0sGlRHD7X1cLyJ3?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/iR3wOu8lejLfbs3H06AbqTKhUFbHHzh7ZQ_bYBeRP_M1nBs5AiKiz_RbxfyTGK60d-fId9_-KtZiRunPwm9hhpXujVFaLxIQSKEeNQqO56_vUeDybsjoX3vNARJTG4Ae5jMEd89hmf1-YzD6UDM8lhqwUuz6QdmeQn5iCQwI2GHkZJNbRqabFHsiSnUYjs87?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/abNbVpWgajOLoEnC9nYwbvtNkjQ7rWgwF7Fi_w1WSTw848LTl_vgaRnRdd-MZ-xKufVHWQiTDhUQRxbzF-1lZmNvDcVq40mnIuX6uviBktjbAzQxjkv4dNtx8dk7Ml3ccAVUOHrW5LgNo4phNH0yjT3soD7doIiOpS6kf7ymP8aYumaIV7Txm5GENJkUeVSF?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/gJsUfM6PsMg3oX-VP4BzgA9bpfKdK2Z1dPpnmozblPITNOEMblxyAF46HqlpPqIEEE4zcekU3zZq0C-JlMX0of6yvrE5dyp2NNwjI22PtE7rHY2Ypfzh88gaCUVhIaQgRVLBoKLsDCj3NymzL3IwZWAfoKNMJ8FGAO5-uB1nirGCSY037uSApR1Z__n_1eDb?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/oRKbnj6tQa4qjceIpncQzyTPsLPLVCqCUesjw0fzfKiRahsrEBvhSnH2dMNjWhYQzudsPYUx4gOKuXaCqYyqWW6MCDwLYBJeDf51nc8u6avPEjIhnVxzkiYEiljM5bB7RDQ5JkvlyL_whC14pWUHHEKy2EiC4IaUYvOVdrPNglGpxtOXK9yfzP3jzFaDUfAC?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/cl60DEAKzM4aGCgrhyH3Qvoum1xUTaVQtTkXY_iI5EOlVe313XPrQqcyvkNbIyihiq3Od-iLr8CXUaP6tNm7ymoobhSGoFf5-oqtrPeudla3rMdHL3yroScJv6JKClHM8D4hVaIk_WSMFlUS_VE3bOvWrFYAOPjIbL1fr_a7_jKLTM9RFCxm_07i4RTOHl6m?purpose=fullsize)

---

# 🔑 Step 3 — Connect to Ubuntu EC2

Use your AWS PEM key:

```bash
ssh -i YOGESH.pem ubuntu@184.72.111.80
```

Successful login output:

```text
Welcome to Ubuntu 26.04 LTS
```

---

# 📤 Step 4 — Copy Public Key to Server

Transfer the public key (`john.pub`) from local machine to EC2:

```bash
scp -i YOGESH.pem john.pub ubuntu@184.72.111.80:/home/ubuntu
```

If prompted:

```text
Are you sure you want to continue connecting?
```

Type:

```text
yes
```

---

## 📸 SCP File Transfer

![Image](https://images.openai.com/static-rsc-4/aquiQ0IVeiznvOQqhDTfbTl0y81FZjlrx27-P62fOiO0963VJ_iCakOz2tTM6NeWU_nHVkBZISfqYR6WdX5gcfHoC_2nUIZF_9ezMFseyoZdcIxXRmf4CagHM5g47zbGjCIkdewOuri0Q9xUeeyi63Rmd6vz2FCIjSduyKzKjNUsSyLgWRj3BMVkQOtZnxp6?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/ACN7JJ0x0km6ntqXgbH_HRShAXh1bUTmYLRkXfhYozflY6o6FRqLW2GYaR9lh5wRzB7pZeJE6FQ6PMqJ58rRyalQWAimKYDDqagWIEHr3YDH-tGQWu0TBh6O2GY03Lw78MKkjyV4IB4DwabmapX6-ai2FESrfaIENvQIS9C3vRTnlLjDnQ_vPzma3MqGZWZ7?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/a8mkAFHp_XIhc89HDWsuUj5OdRbsCsr2KkH5OlWgqdWkLi46Ooy3WMURzRctQvljIJ17HBgPiu10WnAlIOCpPpx16T6BrbxksIPDRaTH-rBaDDRrIf7GoWr2pMnjDnyyXihe9pvOKAmdfH7soATa3KM1vrMGBH4qog7Qd4T-67_0P2ojjjIUzuAzaAy00Av5?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/3uUfElavHvUXkWUuN1Ie6tEkOGcMpM5a-kYtvDwVuNhwe7zUPNqBdEKiI6_lUeGmgjljNCfjOZatwWCWZAh8f9CE97sYD1KkeEBhp7CYjj_slI5IdCh0QU7oXjCe8ISWNsTIDlD8-Tj3Kz1imx5iaS2nT4FI_hkFBJnQx1KtaGkjlH2bEhc8qw8p75IbyeRN?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/ozpoGsMDESrns1v18MaEUlVQljUu277F0Korfnt9KDlBBzz2byYAaTbkE2_eOS_UfeOTmaPdNZC6niOscA3U-OZLfZxO0TOOnQViuXEBH_HZOGfOypnty88kQXwC9PefP9r3CHCLcaY-gAXylas2pKp_cK0fxsASq_OubkB-FV0MOJ92vnufnWmM4dGE_eKq?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/OqCWlbz15NMkP0dROvVTE7OxtAxu-a-qA9iIfNotqeIMOaSPTiVSGGNPvGCobvn7O2wb4czc5gW0vuu-JgM9Q93CvlnXg1bchUT5lXwTL3hDahKeFjzhqpsHunHqt2mqcsfhYIaGrRNnSN_pl-GZ1uul9ZfHXNwImPEzA3qCBdD5QOIMaEwlJY6eSYm8q-An?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/8V5606dMNOoyY6kd14jlNi9-o6wcWPb6Cfq2GQYIJINbSS27sjgAbzmclUVhd7VmbR9kX3pAOp4plbATlQokX6AnmCirnR7rk1Yg_xFg2uDHIh9uOeYZxmQbwHxjJ7uornVbmEt_W4BP5PUlaAbdPCXeNYuoFzxxRra5GhRRqX8Jb6hsZPoiZf4fofumx7OE?purpose=fullsize)

---

# 📁 Step 5 — Verify Public Key on Server

After login, verify the file exists:

```bash
ls -l /home/ubuntu
```

Expected output:

```text
john.pub
```

---

# 👤 Step 6 — Login Using Generated SSH Key

Use the generated private key:

```bash
ssh -i john yogesh@184.72.111.80
```

Successful login:

```text
yogesh@ip-172-31-84-6:~$
```

---

## 📸 Successful SSH Login

![Image](https://images.openai.com/static-rsc-4/rfUX1wdrAIWHM1g84lyI206fuHGZiKDMV0DYx1SAqkuxZgi7GTVgMKpamAObHyYGk50W5J5I_KmQAkLCdaW4XSszchc21lKdxw3A4yNzqOxQfLohCZnfn47rklOJ2lu7Rb7xvYIQz1BvgAEhwUlbZvl7eJzqzkXYZU0wEG5IQUrSt--zBgG5Mnuoyu8_dMzQ?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/HMFMyZo8WskXfLd6PMPzTIUD1sqKHDsIndikN8FLVMXhrIKr1GA3H0wFAH1xKczEa69mvTaolveRBycTBAV_6Lnyd2hEcAZPpg2piKJGJZ7YuKMpDYXsezYwMzL2ldPzvzDHPWjnwC1gXXgnkaXPc0rloBy4MmYxSLfDFTfbZkanFNkJQ8JrLFPlAu52gjEN?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/9jyctUFnJtkPm58ma3byPJ-QtZEkjaQrXqyve_eOs64iNacLSVDl7jV-FGu68hk1S_1QbKPEtiXTGKjEYGvLR2oS9G0NTv2dIwZjVm98ARcF3AbbsVxUPszUEk8dnGs1P2_bGd1Txdxqej9TacZkfbTENoBN2p9slR1_zOs9ZEPtB_rJoeVt13yMhojyWxNz?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/OHuIp11hJHv9wIkDsn-l65HwEYlkH__96FX_ACOOfs3hEHC1YNCAaREkTBwPwGtfNuCgRvNWsK84QG-OdRCupw_vlpEm1PJkMCJQVggE959qjMrTjLydpDs36fp9g7WWOKmhB6uKWFkxnZOxBJ8pvutG5cBKZj5peCbAKWv3c-y8bjY-oqezW1H0bRa_8sMs?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/pIaCfQfXFSzdihYKjZVE4EjUGdL_uceSpXjEHGMsrOmEKQnrh10qfG1-er9q0dRDbU_8CSxO1aUbI9_HEiCCY_NJz5Ukcyza9N25-tgYRihdu81-IkEWW-shNrV_6YUEKUrA1NO3vOGE-qX5WQwU0ofvwKtn1hLCsKdaf6oUtyG44fTxjfE6x8V2BXitig7Z?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/eXgB1IJlBbnI2IxDDPY5utIB-IS0bLC42sd291ua97_aaxrZfdqdzmtNJaZkWtt2ZE7uWxIj2bAIL7FjxRSabPqA2yqvjDz7teTjgvXGy9v6Xmv8sDm2YCKGlt_3lH8CgIu3551MKYp80SXiwyH34VBYMplkoFRtO8BYUEFMimy-sGvrVIirFd-Lz3bUV7kl?purpose=fullsize)

---

# 🛠 Commands Used

```bash
# Move to Downloads folder
cd Downloads

# Generate SSH key pair
ssh-keygen

# Copy public key to EC2
scp -i YOGESH.pem john.pub ubuntu@184.72.111.80:/home/ubuntu

# Connect to EC2 using AWS PEM key
ssh -i YOGESH.pem ubuntu@184.72.111.80

# Verify file
ls -l /home/ubuntu

# Login using generated private key
ssh -i john yogesh@184.72.111.80
```

---

# 📌 Important Notes

* `john` → Private key (Keep Secret 🔒)
* `john.pub` → Public key (Can be shared)
* Never share your private key publicly
* SSH keys are more secure than passwords

---

# 🏁 Conclusion

This practical demonstrates secure SSH authentication using key-based login in AWS EC2.

### ✅ What We Learned

* Generate SSH key pair using `ssh-keygen`
* Transfer public key using `scp`
* Connect securely to Ubuntu EC2
* Verify files on Linux server
* Login using custom SSH private key

This is one of the most important real-world Linux and DevOps administration practices used in production environments.
