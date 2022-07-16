## Must include initial sub text in macro as shown below ##

        Sub Stroke_Volume ()
	
## Data pad set up ##

        Call Doc.OpenView ("Data Pad")

        ' Begin DataPadColumnSetup
        Column = 1
        FunctionType = "Time"
        Channel = ##Stroke Volume Channel##
        RecordMode = 1
        Options = ""
        Call Doc.DataPadColumnSetup (Column, FunctionType, Channel, RecordMode, Options)
        ' End DataPadColumnSetup

        ' Begin DataPadColumnSetup
        Column = 2
        FunctionType = "Selection Start"
        Channel = ##Stroke Volume Channel##
        RecordMode = 1
        Options = ""
        Call Doc.DataPadColumnSetup (Column, FunctionType, Channel, RecordMode, Options)
        ' End DataPadColumnSetup

        ' Begin DataPadColumnSetup
        Column = 3
        FunctionType = "Selection End"
        Channel = ##Stroke Volume Channel##
        RecordMode = 1
        Options = ""
        Call Doc.DataPadColumnSetup (Column, FunctionType, Channel, RecordMode, Options)
        ' End DataPadColumnSetup

        ' Begin DataPadColumnSetup
        Column = 4
        FunctionType = "Selection Duration"
        Channel = ##Stroke Volume Channel##
        RecordMode = 1
        Options = ""
        Call Doc.DataPadColumnSetup (Column, FunctionType, Channel, RecordMode, Options)
        ' End DataPadColumnSetup

        ' Begin DataPadColumnSetup
        Column = 5
        FunctionType = "Mean"
        Channel = ##Stroke Volume Channel##
        RecordMode = 1
        Options = ""
        Call Doc.DataPadColumnSetup (Column, FunctionType, Channel, RecordMode, Options)
        ' End DataPadColumnSetup
        
## Turn Remaining Channels off ##

        ' Begin DataPadColumnSetup
        Column = 6
        FunctionType = "{00000000-0000-0000-0000-000000000000}-0"
        Channel = 5
        RecordMode = 1
        Options = ""
        Call Doc.DataPadColumnSetup (Column, FunctionType, Channel, RecordMode, Options)
        ' End DataPadColumnSetup

        ' Begin DataPadColumnSetup
        Column = 7
        FunctionType = "{00000000-0000-0000-0000-000000000000}-0"
        Channel = 6
        RecordMode = 1
        Options = ""
        Call Doc.DataPadColumnSetup (Column, FunctionType, Channel, RecordMode, Options)
        ' End DataPadColumnSetup

        ' Begin DataPadColumnSetup
        Column = 8
        FunctionType = "{00000000-0000-0000-0000-000000000000}-0"
        Channel = 7
        RecordMode = 1
        Options = ""
        Call Doc.DataPadColumnSetup (Column, FunctionType, Channel, RecordMode, Options)
        ' End DataPadColumnSetup

        ' Begin DataPadColumnSetup
        Column = 9
        FunctionType = "{00000000-0000-0000-0000-000000000000}-0"
        Channel = 8
        RecordMode = 1
        Options = ""
        Call Doc.DataPadColumnSetup (Column, FunctionType, Channel, RecordMode, Options)
        ' End DataPadColumnSetup

        ' Begin DataPadColumnSetup
        Column = 10
        FunctionType = "{00000000-0000-0000-0000-000000000000}-0"
        Channel = 9
        RecordMode = 1
        Options = ""
        Call Doc.DataPadColumnSetup (Column, FunctionType, Channel, RecordMode, Options)
        ' End DataPadColumnSetup

        ' Begin DataPadColumnSetup
        Column = 11
        FunctionType = "{00000000-0000-0000-0000-000000000000}-0"
        Channel = 10
        RecordMode = 1
        Options = ""
        Call Doc.DataPadColumnSetup (Column, FunctionType, Channel, RecordMode, Options)
        ' End DataPadColumnSetup

        ' Begin DataPadColumnSetup
        Column = 12
        FunctionType = "Selection End"
        Channel = 11
        RecordMode = 1
        Options = ""
        Call Doc.DataPadColumnSetup (Column, FunctionType, Channel, RecordMode, Options)
        ' End DataPadColumnSetup

        ' Begin DataPadColumnSetup
        Column = 12
        FunctionType = "{00000000-0000-0000-0000-000000000000}-0"
        Channel = 11
        RecordMode = 1
        Options = ""
        Call Doc.DataPadColumnSetup (Column, FunctionType, Channel, RecordMode, Options)
        ' End DataPadColumnSetup

        ' Begin DataPadColumnSetup
        Column = 13
        FunctionType = "{00000000-0000-0000-0000-000000000000}-0"
        Channel = 12
        RecordMode = 1
        Options = ""
        Call Doc.DataPadColumnSetup (Column, FunctionType, Channel, RecordMode, Options)
        ' End DataPadColumnSetup

        ' Begin DataPadColumnSetup
        Column = 6
        FunctionType = "Full Comment Text"
        Channel = 2
        RecordMode = 1
        Options = ""
        Call Doc.DataPadColumnSetup (Column, FunctionType, Channel, RecordMode, Options)
        ' End DataPadColumnSetup

        Call Doc.OpenCloseWindow ("Data Pad", 1, False)
        Call Doc.SetViewState ("Data Pad", 1, 61728)

## Set cursor to beginning of data ##

        ' Begin SetSelection
        Set selobj = CreateObject("ADIChart.Selection")
        Call selobj.SetSelectionRange (0, 0, 0, 1)
        Call selobj.SetChannelRange (0, 1, -1)
        Call selobj.SetChannelRange (1, 1, -1)
        Call selobj.SetChannelRange (2, 1, -1)
        Call selobj.SetChannelRange (3, 1, -1)
        Call selobj.SetChannelRange (4, 1, -1)
        Call selobj.SetChannelRange (5, 1, -1)
        Call selobj.SetChannelRange (6, 1, -1)
        Call selobj.SetChannelRange (7, 1, -1)
        Call selobj.SetChannelRange (8, 1, -1)
        Doc.SelectionObject = selobj
        ' End SetSelection

        Call Doc.SetViewState ("Chart View", 1, 61488)
        
## Find comment or point in data file for data to begin ##

        ' Begin Find
        ChannelIndex = ##Stroke Volume Channel##
        SetAction = kSetActivePoint
        SelectMode = kSelectAround
        SelectTime = 1
        DataDisplayMode = kViewDataVisible
        SelectAll = False
        Direction = kSearchForward
        FindType = "Search for comment"
        FindData = "JustThisChannel=0;WhatToLookFor=##Comment Name##;"
        Call Doc.Find (ChannelIndex, SetAction, SelectMode, SelectTime, DataDisplayMode, SelectAll, Direction, FindType, FindData)
        ' End Find
        
## Set amount of time to move forward or backward in data file ##

        ' Begin Find
        ChannelIndex = ##Stroke Volume Channel##
        SetAction = kSetToPreviousPoint
        SelectMode = kSelectAround
        SelectTime = 1
        DataDisplayMode = kViewDataVisible
        SelectAll = False
        Direction = kSearchForward
        FindType = "Move forward"
        FindData = "AmountToMove=##Time to move forward or backward##;"
        Call Doc.Find (ChannelIndex, SetAction, SelectMode, SelectTime, DataDisplayMode, SelectAll, Direction, FindType, FindData)
        ' End Find

        Call Doc.AddToDataPad ()

## Repeat as necessary ##

        Call Doc.AddToDataPad ()
        Call Doc.OpenView ("Data Pad")
        Call Doc.SetViewState ("Comments View", 1, 61728)

        End Sub
