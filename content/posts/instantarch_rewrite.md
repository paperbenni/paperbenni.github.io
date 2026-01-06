---
date: '2025-08-30T14:14:32Z'
draft: false
title: 'Instantarch_rewrite'
showToc: true
---

## Edit

This is an early draft of what the new `ins arch` instantOS installer actually
became. The new installer works a bit different but is inspired by this scribble
I did on my phone. 


## Post

This is written on my phone, really quick,
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
password: string
}


trait AskStep {
    fn collect_choices
    fn validate
    fn prompt
}




struct AskStepInfo {
    optional: bool
    AskStepType
}

enum Question {
    Input { default: Option<string> }
    SelectMultiple { choices }
    SelectOne { choices }
    YesNo
}

struct QuestionData {
choices: map(QuestionType, data)
answers: map(QuestionType, answer)
}


Enum QuestionType {
    UserName(UserNameQuestion),
    UserPassword(PasswordQuestion)
}

```


# Alternative approach

```
type StepId = string

answerRegistry = Map<AnswerKind, Answer>
ActiveQuestions = [AnswerKind]
NodeRegistry = [AnswerKind, Node]

build_dependencies
while get_unsatisfied(unsatisfied)
    for step in step
        if step.conditions.active
            if step.unanswered
                return step


struct stepCondition
    ValueEquals(stepID, val)
    ValueNot(stepID, val)
    ValueIn(stepID, vec val)



goback()
    for answer in get_active()
        if active[i+1] == currentstep
            currentstep = active[i]

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
        YesNo
            data = gum ask
        SelectOne
            data = gum choose get_choices
            verify
        SelectMultiple
            data = gum choose get_choices
            verify


struct Step {
    junction: Option<Vec<AskDependency>>,
    question: Option<Leaf(askstuff)>
}


struct AskDependency {
    name: string
    dependencies: [dependency]
}



partitionconfig depends on
rootpartition
bootloaderpartition

fn get_unsatisfied(ActiveQuestions, NodeRegistry)
    sort active_questions by leaf first, junction second
    for question in active_questions
        if question.unsatisfied
            return question

    


```


# tech stack

duct for commands
gum for UI


