# Introduction

Welkom in de wereld van Git. Ik hoop dat dit document u de onderliggende eenvoud van dit krachtige content tracking systeem beter kan laten begrijpen ondanks het duizelingwekkend aantal mogelijkheden die Git van buitenaf lijkt aan te bieden.

Laten we eerst een paar termen doornen die doorheen de tekst voorkomen:

* **repository** — Een **repository** is een verzameling _commits_, elk een archief van de _working tree_ op een vroegere datum - op uw eigen machine of dat van iemand anders. Het definieert ook HEAD (zie verder), wat aanduidt van welke branch of commit de huidige working tree afstamt. Tot slot bevat het een set van _branches_ en _tags_ om bepaalde commits bij naam te kunnen noemen.

* de **index** - Git schrijft veranderingen van de _working tree_ niet onmiddellijk in de _repository. Veranderingen worden eerst geregistreerd in wat men de **index** noemt. Je kan het beschouwen als een manier om je wijzigingen, één voor één, te bevestigen voordat je een commit doet (dewelke in één keer al je goedgekeurde wijzigingen onthoudt). Sommigen noemden de index liever de  “staging area”.

* **working tree** — A **working tree** is any directory on your filesystem which has a _repository_ associated with it (typically indicated by the presence of a sub-directory within it named `.git`.). It includes all the files and sub-directories in that directory.

* **commit** — A **commit** is a snapshot of your working tree at some point in time. The state of HEAD (see below) at the time your commit is made becomes that commit’s parent. This is what creates the notion of a “revision history”.

* **branch** — A **branch** is just a name for a commit (and much more will be said about commits in a moment), also called a reference. It’s the parentage of a commit which defines its history, and thus the typical notion of a “branch of development”.

* **tag** — A **tag** is also a name for a commit, similar to a _branch_, except that it always names the same commit, and can have its own description text.

* **master** — The mainline of development in most repositories is done on a branch called “**master**”. Although this is a typical default, it is in no way special.

* **HEAD** — **HEAD** is used by your repository to define what is currently checked out:
  * If you checkout a branch, HEAD symbolically refers to that branch, indicating that the branch name should be updated after the next commit operation.
  *  If you checkout a specific commit, HEAD refers to that commit only. This is referred to as a detached _HEAD_, and occurs, for example, if you check out a tag name.

The usual flow of events is this: After creating a repository, your work is done in the working tree. Once your work reaches a significant point — the completion of a bug, the end of the working day, a moment when everything compiles — you add your changes successively to the index. Once the index contains everything you intend to commit, you record its content in the repository. Here’s a simple diagram that shows a typical project’s life-cycle:

![Project Lifecycle](images/lifecycle.png)

With this basic picture in mind, the following sections shall attempt to describe how each of these different entities is important to the operation of Git.
