# powerapps-shuffled-virtual-keyboard
This repository consists code for the demo that shows how to add a shuffled virtual keyboard for password entry (digits)

//App OnStart Code

ClearCollect(
    ShuffledItems,
    [
        "1",
        "2",
        "3",
        "4",
        "5",
        "6",
        "7",
        "8",
        "9",
        "0",
        "Delete",
        "✓"
    ]
);


//Gallery Items Code

ShuffledItems

// Gallery Buttons Code

Switch(

    //Condition to check value
    
    ThisItem.Value,

    //If it is delete
    
    "Delete",
    
    Remove(SelectedValues,Last(SelectedValues)),

    //If it is check mark
    
    "✓",
    
    Set(HideVirtualKeyboard,true),
    
    //If it is neither delete nor check mark
    
    Collect(SelectedValues,ThisItem.Value);
    
    ClearCollect(ShuffledItems,Shuffle(["1","2","3","4","5","6","7","8","9","0"]));
    
    Collect(ShuffledItems,["Delete"],["✓"])
    
)

// Label Code

Concat(SelectedValues.Value,Value,"     ")

