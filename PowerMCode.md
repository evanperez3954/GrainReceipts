Agtrax BI DateDim

let Source = PowerPlatform.Dataflows(null), Workspaces = Source{[Id="Workspaces"]}[Data], #"f5c6218e-9b50-4e8b-87fc-7d5f7d56dabe" = Workspaces{[workspaceId="f5c6218e-9b50-4e8b-87fc-7d5f7d56dabe"]}[Data], #"ca05a624-6d51-4089-952a-08addb11ade2" = #"f5c6218e-9b50-4e8b-87fc-7d5f7d56dabe"{[dataflowId="ca05a624-6d51-4089-952a-08addb11ade2"]}[Data], #"Agtrax BI DateDim_" = #"ca05a624-6d51-4089-952a-08addb11ade2"{[entity="Agtrax BI DateDim",version=""]}[Data], #"Filtered Rows" = Table.SelectRows(#"Agtrax BI DateDim_", each [Date1] >= #date(2022, 1, 1)) in #"Filtered Rows"


Grain Receipt Summary

let Source = PowerPlatform.Dataflows(null), Workspaces = Source{[Id="Workspaces"]}[Data], #"f5c6218e-9b50-4e8b-87fc-7d5f7d56dabe" = Workspaces{[workspaceId="f5c6218e-9b50-4e8b-87fc-7d5f7d56dabe"]}[Data], #"8b10c865-e7c8-44f1-b47d-ae56f5bb64d6" = #"f5c6218e-9b50-4e8b-87fc-7d5f7d56dabe"{[dataflowId="8b10c865-e7c8-44f1-b47d-ae56f5bb64d6"]}[Data], #"Grain Receipt Summary_" = #"8b10c865-e7c8-44f1-b47d-ae56f5bb64d6"{[entity="Grain Receipt Summary",version=""]}[Data], #"Renamed Columns" = Table.RenameColumns(#"Grain Receipt Summary_",{{"FISCAL_YEAR", "Fiscal Year"}, {"BRANCH_NAME", "Location"}, {"CUSTOMER_NAME_RU", "Account Name"}, {"CROP_NAME", "Crop"}}), #"Capitalized Each Word" = Table.TransformColumns(#"Renamed Columns",{{"Account Name", Text.Proper, type text}, {"Crop", Text.Proper, type text}, {"Location", Text.Proper, type text}}) in #"Capitalized Each Word"


LocationsMaster

let Source = PowerPlatform.Dataflows(null), Workspaces = Source{[Id="Workspaces"]}[Data], #"f5c6218e-9b50-4e8b-87fc-7d5f7d56dabe" = Workspaces{[workspaceId="f5c6218e-9b50-4e8b-87fc-7d5f7d56dabe"]}[Data], #"6a40dd86-067b-48fd-9e96-a92748c5569a" = #"f5c6218e-9b50-4e8b-87fc-7d5f7d56dabe"{[dataflowId="6a40dd86-067b-48fd-9e96-a92748c5569a"]}[Data], LocationsMaster_ = #"6a40dd86-067b-48fd-9e96-a92748c5569a"{[entity="LocationsMaster",version=""]}[Data], #"Split Column by Delimiter" = Table.SplitColumn(LocationsMaster_, "Latitude & Longitude", Splitter.SplitTextByDelimiter(",", QuoteStyle.Csv), {"Latitude & Longitude.1", "Latitude & Longitude.2"}), #"Changed Type" = Table.TransformColumnTypes(#"Split Column by Delimiter",{{"Latitude & Longitude.1", type number}, {"Latitude & Longitude.2", type number}}), #"Renamed Columns" = Table.RenameColumns(#"Changed Type",{{"Latitude & Longitude.1", "Latitude"}, {"Latitude & Longitude.2", "Longitude"}}), #"Changed Type1" = Table.TransformColumnTypes(#"Renamed Columns",{{"Latitude", type number}, {"Longitude", type number}}) in #"Changed Type1"

Grain Balances

let
    Source = PowerPlatform.Dataflows(null),
    Workspaces = Source{[Id="Workspaces"]}[Data],
    #"f5c6218e-9b50-4e8b-87fc-7d5f7d56dabe" = Workspaces{[workspaceId="f5c6218e-9b50-4e8b-87fc-7d5f7d56dabe"]}[Data],
    #"8b10c865-e7c8-44f1-b47d-ae56f5bb64d6" = #"f5c6218e-9b50-4e8b-87fc-7d5f7d56dabe"{[dataflowId="8b10c865-e7c8-44f1-b47d-ae56f5bb64d6"]}[Data],
    GrainBalances_ = #"8b10c865-e7c8-44f1-b47d-ae56f5bb64d6"{[entity="GrainBalances",version=""]}[Data],
    #"Capitalized Each Word" = Table.TransformColumns(GrainBalances_,{{"CUSTOMER_NAME", Text.Proper, type text}, {"COMMODITY_DESC", Text.Proper, type text}, {"BRANCH_NAME", Text.Proper, type text}, {"CROP_DESC", Text.Proper, type text}})
in
    #"Capitalized Each Word"