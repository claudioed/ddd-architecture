## Transaction Monitoring

```mermaid
classDiagram
    class Transaction {
        +String TransactionID
        +Money Amount
        +Timestamp Timestamp
        +Account SourceAccount
        +Account DestinationAccount
        +String TransactionType
        +String Status
        +ValidateTransaction()
        +MarkAsSuspicious()
        +ApproveTransaction()
        +RejectTransaction()
    }

    class Alert {
        +String AlertID
        +String TransactionID
        +String AlertType
        +String Severity
        +Timestamp Timestamp
        +String Status
        +GenerateAlert()
        +EscalateAlert()
        +ResolveAlert()
    }

    class LogEntry {
        +String LogID
        +String TransactionID
        +String Message
        +Timestamp Timestamp
        +String LogLevel
        +CreateLogEntry()
        +RetrieveLogEntries()
    }

    class SecurityInvestigation {
        +String InvestigationID
        +String AlertID
        +String InvestigatorID
        +String Findings
        +String Status
        +Timestamp Timestamp
        +InitiateInvestigation()
        +UpdateInvestigation()
        +CloseInvestigation()
    }

    class Account {
        +String AccountID
        +String AccountHolderName
        +String AccountType
    }

    class Money {
        +float Amount
        +String Currency
    }

    class Timestamp {
        +String Date
        +String Time
    }

    Transaction --> Account : SourceAccount
    Transaction --> Account : DestinationAccount
    Transaction --> Money : Amount
    Transaction --> Timestamp : Timestamp

    Alert --> Timestamp : Timestamp

    LogEntry --> Timestamp : Timestamp

    SecurityInvestigation --> Timestamp : Timestamp
    SecurityInvestigation --> Alert : AlertID
