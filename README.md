## Git Impressions
- It is a good start of adventures with GIT :)

## Unix Shell
![Unix](task_unix_shell/linux_done.png)


## Git Collaboration
- Enjoyed with lessons. 
Structured materials helped to refresh some gaps (example, with rebasing :)

![GIT](task_git_collaboration/git_1.png)

![GIT](task_git_collaboration/git_2.png)

![GIT](task_git_collaboration/git_3.png)


## Memory Management
- [X] What's going to happen if program reaches maximum limit of stack ?

    If the maximum stack size has been reached, we have a stack overflow and the program receives a Segmentation Fault. 

- [X] What's going to happen if program requests a big (more then 128KB) memory allocation on heap ?

    It will create an anonymous mapping instead of using heap memory. 
    Anonymous mapping that does not correspond to any files, 
    being used instead for program data.

- [X] What's the difference between Text and Data memory segments ?

    A text segment  is one of the sections of a program in an object file or 
    in memory, which contains executable instructions. Usually, the text segment is sharable so that 
    only a single copy needs to be in memory for frequently executed programs, such as text editors, 
    the C compiler, the shells, and so on. Also, the text segment is often read-only, 
    to prevent a program from accidentally modifying its instructions.

    Data segment is a portion of virtual address space of a program, which contains the global variables 
    and static variables that are initialized or not initialized (BSS) by the programmer.
    Data segment is not read-only, since the values of the variables can be altered at run time.

    - [X] Result of vmmap command
    
    **Heap** - 55f16c1b6000-55f16c1d7000, **Stack** - 7ffddb215000-7ffddb236000, **MMS** - 7fd078843000-7fd078a2a000.
    
```
alaty@quebec:~/Desktop/kottans-backend$ ps -a | grep pycharm
 8536 tty2     00:00:00 pycharm.sh
alaty@quebec:~/Desktop/kottans-backend$ cat /proc/8536/maps
55f16ad0d000-55f16ad29000 r-xp 00000000 fd:01 14549026                   /bin/dash
55f16af28000-55f16af2a000 r--p 0001b000 fd:01 14549026                   /bin/dash
55f16af2a000-55f16af2b000 rw-p 0001d000 fd:01 14549026                   /bin/dash
55f16af2b000-55f16af2d000 rw-p 00000000 00:00 0 
55f16c1b6000-55f16c1d7000 rw-p 00000000 00:00 0                          [heap]
7fd078843000-7fd078a2a000 r-xp 00000000 fd:01 2888391                    /lib/x86_64-linux-gnu/libc-2.27.so
7fd078a2a000-7fd078c2a000 ---p 001e7000 fd:01 2888391                    /lib/x86_64-linux-gnu/libc-2.27.so
7fd078c2a000-7fd078c2e000 r--p 001e7000 fd:01 2888391                    /lib/x86_64-linux-gnu/libc-2.27.so
7fd078c2e000-7fd078c30000 rw-p 001eb000 fd:01 2888391                    /lib/x86_64-linux-gnu/libc-2.27.so
7fd078c30000-7fd078c34000 rw-p 00000000 00:00 0 
7fd078c34000-7fd078c5b000 r-xp 00000000 fd:01 2888363                    /lib/x86_64-linux-gnu/ld-2.27.so
7fd078e3d000-7fd078e3f000 rw-p 00000000 00:00 0 
7fd078e5b000-7fd078e5c000 r--p 00027000 fd:01 2888363                    /lib/x86_64-linux-gnu/ld-2.27.so
7fd078e5c000-7fd078e5d000 rw-p 00028000 fd:01 2888363                    /lib/x86_64-linux-gnu/ld-2.27.so
7fd078e5d000-7fd078e5e000 rw-p 00000000 00:00 0 
7ffddb215000-7ffddb236000 rw-p 00000000 00:00 0                          [stack]
7ffddb2a8000-7ffddb2ab000 r--p 00000000 00:00 0                          [vvar]
7ffddb2ab000-7ffddb2ac000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]

```

Memory management is too useful topic for learning.
In spite of we are working with program languages ​​which has garbage collector which makes our life easier,
we need to keep in mind how memory is used and which problem can occur in case of incorrect using it to prevent memory
leaks and other possible problems. Tasks contain description of different memory segments, what type of data
is stored there, which errors occur in case of using more memory than allowed. 
P.S. I have a new goal - be better in understanding of memory usage. It is task for future improvement :)


## Http & Https
Additional tasks:
1. List repositories of "Kottans" organization:
    ```
    curl -i https://api.github.com/orgs/kottans/repos
   ```

2. Create new issue in my repository:
    ```
    curl -i -u AnastasiiaLatysh -d '{"title": "Kottans backend issue", "body": "Http & Https",
    "labels": ["bug"] }' https://api.github.com/repos/AnastasiiaLatysh/kottans-backend/issues
    ```
Questions:
1. Name at least three possible negative consequences of not using https:
     - server is not authenticated;
     - data transmission is not encrypted;
     - absence of protecting the exchanges from tampering.

2. Explain the main idea behind public key cryptography in few sentences.

    Public key cryptography is an encryption technique that uses a paired public and private key (or asymmetric key)
    algorithm for secure data communication. A message sender uses a recipient's public key to encrypt a message.
    To decrypt the sender's message, only the recipient's private key may be used.

3. You are creating and application for pet clinic. You need to implement the following functionality:
    
    - Add new pet (including name, age, breed, owner's name, medical history)
    
        **Request**
        
        POST /api/v1/pet/
        
        <details>
        <summary>Request body</summary>
        
        ```
        {
        "name": "Jack",
        "age": 2,
        "breed": "labrador",
        "owner_name": "Alica",
        "medical_history": ""
        }
        ```
        </details>
        
        **Response**
        
        Status code: 201 - Created
        
        <details>
        <summary>Response body</summary>
        
        ```
        {
        "id": 1,
        "name": "Jack",
        "age": 2,
        "breed": "labrador",
        "owner_name": "Alica",
        "medical_history": ""
        }
        ```
        </details>
    
    - Search pet by name
    
        **Request**
        
        GET /api/v1/pet/?name=Jack
        
        **Response**
        
        Status code: 200 - OK
        
        <details>
        <summary>Response body</summary>>
        
        ```
        {
        "id": 1,
        "name": "Jack",
        "age": 2,
        "breed": "labrador",
        "owner_name": "Alica",
        "medical_history": ""
        }
        ```
        </details>
    
    - Change name of an existing pet
    
        **Request**
        
        PUT /api/v1/pet/
        
        <details>
        <summary>Request body</summary>
        
        ```
        {
        "id": 1,
        "name": "New Jack"
        }
        ```
        </details>
        
        **Response**
        
        Status code: 200 - OK
        
        <details>
        <summary>Response body</summary>
        
        ```
        {
        "id": 1,
        "name": "New Jack",
        "age": 2,
        "breed": "labrador",
        "owner_name": "Alica",
        "medical_history": ""
        }
        ```
        </details>
    
    - Add new info about pet's health
    
        **Request**
        
        PUT /api/v1/pet/
        
        <details>
        <summary>Request body</summary>
        
        ```
        {
        "id": 1,
        "medical_history": "New Jack is healthy"
        }
        ```
        </details>
        
        **Response**
        
        Status code: 200 - OK
        
        <details>
        <summary>Response body</summary>
        
        ```
        {
        "id": 1,
        "name": "New Jack",
        "age": 2,
        "breed": "labrador",
        "owner_name": "Alica",
        "medical_history": "New Jack is healthy"
        }
        ```
        </details>
    
    - Assign a pet to a particular doctor in the clinic
    
        **Request**
        
        POST /api/v1/vet/1/pet/
        
        <details>
        <summary>Request body</summary>
        
        ```
        {"pet_ids": [1]}
        ```
        </details>
        
        **Response**
        
        Status code: 201 - Created
        
        <details>
        <summary>Response body</summary>
        
        ```
        {
        "id": 1,
        "vet_name": "Doctor Aibolit",
        "pet_ids": [1]
        }
        ```
        </details>
    
    - Register an appointment for a pet. This request should include info about pet, doctor and appointment date and time.
    
        **Request**
        
        POST /api/v1/appointment/
        
        <details>
        <summary>Request body</summary>
        
        ```
        {
        "vet_id": 1,
        "pet_id": 1,
        "date": "2019-10-01",
        "time": "14:00"
        }
        ```
        </details>
        
        Response
        
        Status code: 201 - Created
        
        <details>
        <summary>Response body</summary>
        
        ```
        {
        "id": 1,
        "vet_id": 1,
        "pet_id": 1,
        "date": "2019-10-01",
        "time": "14:00"
        }
        ```
        </details>
