---
date: '2025-08-30T14:14:32Z'
draft: true
title: 'Instantarch_rewrite'
showToc: true
---

This is writtrn on my phone, really quick, 
dirty thoughts


```
Rust


installConfig struct

instantosconfig {
    user: userconfig
    partitions: partitionconfig
}

serializable to toml -> reusable

trait from_answers {
    fn from_answer(answers) -> Result Self
}

struct instantOSInstall {
    user: UserConfig

}

UserConfig = {
    username: string
password strung
}


trait AskStep {
    fn collect_choices
    fn validate
    fn prompt
}




struct AskSteoInfo {
    optional: bool
    AskStepType
}

enum Question {
    Input { default: Option<string> }
    SelectMultuple { choices }
    SelectOne { choices }
    YesNo
}

struct QuestuonData {
choices: map(QuestuonRype, data)
answers: map(QurstuinType, answer)
}


Enum QuestionType {
    UserName(usernamequestion),
    UsrrPassword(passwordquestion)
}

```


# Alternative approach

```

answerRegistry = Map<AnswerKind, Answer>
ActiveQuestuons = [AnsswerKind]
NocdeRegustry = [AnswerKind, Node]

build_dependencies
while get_unsatisfied(unsatifyed)
    for leaf in leaves
        answer = askquestion
        match answer {
            Back => goback
            Data => anserstack.push(AnswerKind>
        }
    if junctions.not_empty
        ask junctions[0]
            data =>
                answerstack.push([newdependencies])
                axtivequ3stions.extend(newdependencies)
                deduplicate axtiveanswrrs
            back => goback

goback()
    match answerstack.pop
        junction
            axtiveanswers.remove(junctiondep3ndencies)
        anseer
            answerregistry.remove(answe4kind)

fn cleanDependencies
    if multiple_branches_satisfied:
        choose_branch_to_keep
        remove dependencies of other branches
        readd_dependencies_of_kept_branch


trait Leaf<data>
    data: data
    leafkind: enum
    fn verify
    fn get_choices

enum leafkind
    YesNo
    Input
    ChooseOne
    ChooseMulti
    Custom(lambda stuff)
    
askLeaf(leaf)
    match leafkind
        yesno
            data = gum ask
        selectone
            data = gum choose get_choices
            verify
        selectMultiple
            data = gum choose get_choices
            verify


Step {
    junction(vec<AskDependency>)
    Leaf(askstuff)
}


struxt AskDependenxy {
name: string
dependencies: [dependency]
}





partitionconfig depends on
rootpartition
bootloaderpartition

fn get_unsatisfied(ActiveQuestions, NkdeRegistry)
    sort activequestuins by leaf first, jinction sexond
    for question in activequestions
        if question unsatisfied
            return question

instantosconfig
deoends on
    UserName
    ParitionConfig



```


# tech stack

duct for commands
gum for UI


