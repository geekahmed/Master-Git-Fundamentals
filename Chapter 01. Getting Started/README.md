# Chapter 01. Getting Started
This chapter will be about getting started with Git. We will begin by explaining some background
on version control tools, then move on to how to get Git running on your system and finally how to
get it set up to start working with. At the end of this chapter you should understand why Git is
around, why you should use it and you should be all set up to do so.

## Table of Content
* [About Version Control](#about-version-control)
* [A Short History of Git](#a-short-history-of-git)
* [What is Git?](#what-is-git)
* [First-Time Git Setup](#first-time-git-setup)

### About Version Control
* **What is Version Control?**
    * A system that tracks changes to files (often software code) over time.
    * Allows retrieval of specific past versions as needed.
    * Applicable to diverse file types beyond code (e.g., images, layouts).

* **Why Use Version Control?**
    * **Easy Rollback:**  Revert files or entire projects to previous states.
    * **Change Tracking:** Compare file versions over time.
    * **Collaboration:** Identify who made changes, understand when changes were introduced.
    * **Recovery:** Recover lost or damaged files.
    * **Efficiency:**  Provides these benefits with minimal overhead. 
* **Limitations of Manual Versioning (e.g., copying files)**
    * **Error-prone:**  Easy to overwrite the wrong files or lose track of versions.

* **Local Version Control Systems**
    * **Solution:** Introduce a database to track file changes systematically and reduce errors.
    * **Mechanism:** Store differences between versions ("patch sets") for efficient reconstruction of past file states.
    * **Example:** RCS (Revision Control System), a popular tool for local version control.

<p align="center">
  <img src="./resources/images/Local version control diagram.png" alt="Local version control diagram"/>
</p>

* **Advantages of CVCSs**
    * **Collaboration:** Enables developers on different systems to work together on a project.
    * **Centralized Management:** Provides administrators with fine-grained control over access and simplifies administration compared to local VCSs.

* **Disadvantages of CVCSs**
    * **Single Point of Failure:** Relies on a central server, which can be a bottleneck if it goes down or becomes corrupted.
    * **Data Loss Risk:**  Losing the central server can lead to data loss if proper backups are not maintained.


<p align="center">
  <img src="./resources/images/Centralized version control diagram.png" alt="Centralized version control diagram"/>
</p>

* **How DVCSs Work:**
    * **Full Mirroring:** Clients don't just get the latest file changes; they clone the entire repository with its full history.
    * **Redundancy:** Any client repository can act as a backup, mitigating the risk of a  single point of failure.

* **Advantages of DVCSs**
    * **Resilience:** Less vulnerable to central server failures, improving data security. 
    * **Flexibility:** Supports collaboration with multiple remote repositories and diverse workflows (including hierarchical structures), giving more options compared to centralized systems. 

<p align="center">
  <img src="./resources/images/Distributed version control diagram.png" alt="Distributed version control diagram"/>
</p>

### A Short History of Git
* **Git's History**
    * **Controversy:** Git was born out of necessity when the Linux kernel project lost access to its previous version control tool (BitKeeper).
    * **Creative Response:**  Linus Torvalds and the Linux community were driven to create their own solution tailored to their needs.

* **Git's Design Goals**
    * **Speed:**  Prioritizes performance for fast operations.
    * **Simplicity:**  Focuses on a streamlined design.
    * **Non-linear Development:**  Robust support for extensive branching, ideal for complex projects.
    * **Distributed:** Decentralized architecture for collaboration and resilience. 
    * **Scalability:**  Optimized to handle large-scale projects efficiently. 

### What is Git?
* **How Git is Different**
    * **Snapshots vs. Differences:** Unlike most version control systems that track changes between file versions, Git stores data as a series of snapshots of the entire project's state.
<p align="center">
  <img src="./resources/images/Storing data as changes to a base version of each file.png" alt="Storing data as changes to a base version of each file"/>
</p>


* **Benefits of Snapshots**
    * **Efficiency:** Git avoids storing redundant data; unchanged files are linked rather than re-stored.
    * **Conceptual Model:** Viewing your project history as snapshots offers a different perspective and enables powerful branching features (covered later in the text). 

<p align="center">
  <img src="./resources/images/Storing data as snapshots of the project over time.png" alt="Storing data as snapshots of the project over time"/>
</p>

* **Local Focus:** The majority of Git operations rely solely on local files and data, eliminating network communication in most cases. 
* **Speed Advantage:**  This local approach translates into lightning-fast operations, as there's no need to wait for a server.
* **Offline Capabilities:**  You can work and commit changes to your local repository even without an internet connection or VPN access.
* **Workflow Flexibility:** Git offers a more flexible experience compared to many centralized version control systems that heavily depend on server access. 
* **Checksumming:**  Git calculates a unique checksum (SHA-1 hash) for every piece of data stored (files, directories).
* **Tamper Detection:** Any unauthorized modification to the data is immediately detectable by Git due to a mismatch in the checksum.
* **SHA-1 Hashes:** Git identifies data by its SHA-1 hash (e.g., 24b9da6552252987aa493b52f8696cd6d3b00373) rather than filenames.
* **Reliability:** This mechanism ensures data within Git remains secure and untampered with. 
* **Focus on Addition:** Most Git actions add new data to the repository, making operations easily reversible.
* **Data Safety:** Committed changes are extremely difficult to lose, especially if you push them to a remote repository for backup.
* **Flexibility:** This encourages experimentation and lessens the fear of making irrevocable mistakes. 
* **Three File States**

    * **Modified:**  File has changed, but the changes aren't saved to Git yet.
    * **Staged:**  Modified file is marked for inclusion in the next commit.
    * **Committed:** Changes are safely stored in your local Git database.

* **Project Structure**

    * **Working Tree:**  Current version of your project files on your system.  
    * **Staging Area (Index):**  A holding area for changes to be included in the next commit.
    * **Git Directory:**  The core of your Git repository, storing project metadata and history.

* **Basic Git Workflow**

    1. **Modify:** Edit files in your working tree.
    2. **Stage:** Select specific changes to include in your next commit.
    3. **Commit:**  Permanently save the staged changes as a snapshot in your Git directory. 

<p align="center">
  <img src="./resources/images/Working tree, staging area, and Git directory.png" alt="Working tree, staging area, and Git directory"/>
</p>

### First-Time Git Setup

**Why Configure Git**

* **Commit Attribution:** Git associates your name and email with each saved change (commit).
* **Tool Integration:** Git uses your configuration to interact with text editors and other tools.

**Key Actions**

1. **Set User Identity:**
   * `git config --global user.name "Your Name"`
   * `git config --global user.email your_email@example.com`

2. **Choose Text Editor:**
   *  `git config --global core.editor [editor_name]` 
      * **Windows Note:** Specify the full path to the editor executable.

3. **(Optional) Set Initial Branch Name (Git 2.28+):**
   * `git config --global init.defaultBranch main` 

**Managing Configuration**

* **See All Settings:** `git config --list`
* **Check Specific Setting:** `git config [key_name]`
* **Find Value Origin:** `git config --show-origin [key_name]` 

**Important Notes:**

* The `--global` flag makes settings apply to all projects on your system (current user).
* Configuration files are hierarchical, so later settings override earlier ones. 
