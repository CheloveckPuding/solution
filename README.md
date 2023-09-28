
```python
\\7
def main(s):
    i = int(s)
    h1 = 0b111111111 & i
    h2 = 0b1111111111 & (i >> 9)
    h3 = 0b111 & (i >> 18)
    return tuple(map(str, (h1, h2, h3,)))

#5
import math


def main(y, z):
    sum = 0
    n = len(y)
    y = [0] + y
    z = [0] + z
    for i in range(1, n + 1):
        a = (y[n + 1 - i] ** 3)
        b = (-18 * z[n + 1 - math.ceil(i / 2)] - 71)
        sum += 96 * (a + b) ** 2
    return 86 * sum

#6
def main(x):
    match x[1]:
        case "SMALI":
            match x[0]:
                case 2018:
                    match x[4]:
                        case "UNO":
                            return x21(x)
                        case default:
                            return x41(x)
                case default:
                    return x01(x)
        case "VOLT":
            return x42(x)
        case "XML":
            return 12


def x01(x):
    match x[0]:
        case 2020:
            return 5
        case 1999:
            return 6


def x21(x):
    match x[2]:
        case 2013:
            return 0
        case 2017:
            return 1
        case 1997:
            return 2


def x41(x):
    match x[4]:
        case "PAWN":
            return 3
        case "NINJA":
            return 4


def x42(x):
    match x[4]:
        case "UNO":
            return 7
        case "PAWN":
            return x22(x)
        case "NINJA":
            return 11


def x22(x):
    match x[2]:
        case 2013:
            return 8
        case 2017:
            return 9
        case 1977:
            return 10

#7
def main(number):
    n = int(number, 16)
    return [
        ('01', (n & 1)),
        ('03', ((n >> 5) & 0b11111)),
        ('04', ((n >> 10) & 0b111))
    ]


#10
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



