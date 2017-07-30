`shouldComponentUpdate?`

###### Performance tips and tricks for rendering quick with react

by @aganglada

---

![react](images/react.svg =200px)
![rocket](images/rocket.png =200px)

---

### Initial render

---





-- image of how react tree dom renders
-- image of a change
-- image of how react works by default


---

## How do we get the ideal update?

return false from `shouldComponentUpdate` as high up in your application as you can.

1. Make `shouldComponentUpdate` checks fast
2. Make `shouldComponentUpdate` checks easy

---

## Make `shouldComponentUpdate` checks fast

-- example code of cheking isDeepEqual

---

## Changing references

newValue !== oldValue

---

## Make `shouldComponentUpdate` checks easy

-- reselect
