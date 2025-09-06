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
type StepId = string

answerRegistry = Map<AnswerKind, Answer>
ActiveQuestuons = [AnsswerKind]
NocdeRegustry = [AnswerKind, Node]

build_dependencies
while get_unsatisfied(unsatifyed)
    for step in step
        if step.cinditions.active
            if step.unanswered
                return step


struct stepCondition
    ValueEquals(stepID, val)
    ValueNot(stepID, val)
    ValueIn(stepID, vec val)



goback()
    for answer in get_active()
        if active[i+1] = currentstep
            currentstep = axtice[i]

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


struct Step {
    junction: Option vec<AskDependency>)
    question: Option<Leaf(askstuff)>
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

    


```


# tech stack

duct for commands
gum for UI


