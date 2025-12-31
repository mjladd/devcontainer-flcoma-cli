

# LabelSet
An associative container for identifiers and labels







### LabelSet
IdentifierLabel1trombone2oboe3oboe4trombone5tromboneWe could use this



### DataSet
IdentifierData1132.11323.30424.4420.011.323.1432.111.230.844233.30400.2098.305244.7089.20800.00

## Some Caveats to Remember[](#some-caveats-to-remember)

- Identifiers are unique. You cannot have the same identifier twice in a single
- 
[LabelSet](/reference/labelset).Identifiers and labels are*symbols*. Even if you use a number for either of these, they will be internally represented as a “string” and returned to you as such. This means using`fromsymbol`in Max, for example, if you want the identifier or label to be converted to an actual number.