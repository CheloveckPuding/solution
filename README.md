# solution
```python
from enum import Enum, auto


class MealyError(Exception):
    def __init__(self, *args: object) -> None:
        super().__init__(*args)


class State(Enum):
    A = auto()
    B = auto()
    C = auto()
    D = auto()
    E = auto()
    F = auto()


class FSM:
    def __init__(self):
        self.state = State.A

    def update_state(self, new_state):
        self.state = new_state

    def paste(self):
        match self.state:
            case State.A:
                self.update_state(State.B)
                return 0
            case State.C:
                self.update_state(State.D)
                return 2
            case State.D:
                self.update_state(State.E)
                return 5
            case State.E:
                self.update_state(State.F)
                return 7
            case State.F:
                self.update_state(State.B)
                return 8
            case _:
                raise MealyError("paste")

    def tag(self):
        match self.state:
            case State.B:
                self.update_state(State.C)
                return 1
            case State.C:
                self.update_state(State.E)
                return 4
            case State.D:
                self.update_state(State.A)
                return 6
            case _:
                raise MealyError("tag")

    def split(self):
        match self.state:
            case State.C:
                self.update_state(State.C)
                return 3
            case _:
                raise MealyError("split")


def main():
    return FSM()


def test():
    fsm = main()
    try:
        fsm.split()
    except MealyError:
        pass
    try:
        fsm.tag()
    except MealyError:
        pass
    fsm.paste()
    fsm.tag()
    fsm.split()
    fsm.paste()
    try:
        fsm.split()
    except MealyError:
        pass
    fsm.paste()
    try:
        fsm.tag()
    except MealyError:
        pass
    try:
        fsm.split()
    except MealyError:
        pass
    fsm.paste()
    try:
        fsm.split()
    except MealyError:
        pass
    try:
        fsm.tag()
    except MealyError:
        pass
    fsm.paste()
    try:
        fsm.split()
    except MealyError:
        pass
    try:
        fsm.paste()
    except MealyError:
        pass
    fsm.update_state(State.C)
    fsm.tag()
    fsm.paste()
    fsm.update_state(State.D)
    fsm.tag()


main()
```


