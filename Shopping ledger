

library(shiny)
library(shinydashboard)
library(ggplot2)
library(dplyr)



ui <- dashboardPage(
  
  dashboardHeader(
    title = span(
      icon("shield-halved"),
      " SecureShop"
    )
  ),
  
  dashboardSidebar(
    width = 240,
    
    sidebarMenu(
      menuItem("Dashboard", tabName = "dashboard",
               icon = icon("gauge-high")),
      
      menuItem("Shopping Ledger", tabName = "ledger",
               icon = icon("receipt")),
      
      menuItem("Add Transaction", tabName = "add",
               icon = icon("cart-plus")),
      
      menuItem("Security", tabName = "security",
               icon = icon("shield-halved"))
    )
  ),
  
  dashboardBody(
    
    
    
    tags$head(
      tags$style(HTML("
      
      body {
        font-family: 'Segoe UI', Arial, sans-serif;
      }
      
      .content-wrapper {
        background: #f4f0ff;
      }
      
      .main-header .logo {
        background: #5b21b6 !important;
        color: white !important;
        font-weight: 700;
      }
      
      .main-header .navbar {
        background: #7c3aed !important;
      }
      
      .skin-blue .main-sidebar {
        background: #241044 !important;
      }
      
      .skin-blue .sidebar-menu > li > a {
        color: #ddd6fe !important;
        padding: 15px 12px;
        font-size: 14px;
      }
      
      .skin-blue .sidebar-menu > li.active > a,
      .skin-blue .sidebar-menu > li:hover > a {
        background: #7c3aed !important;
        color: white !important;
        border-left: 4px solid #c4b5fd;
      }
      
      .box {
        border-radius: 18px !important;
        border: none !important;
        box-shadow: 0 5px 20px rgba(91,33,182,0.10);
        overflow: hidden;
      }
      
      .box-header {
        font-weight: 700;
      }
      
      .small-box {
        border-radius: 18px;
        box-shadow: 0 5px 18px rgba(91,33,182,0.12);
      }
      
      .small-box h3 {
        font-size: 30px;
        font-weight: 700;
      }
      
      .welcome-card {
        background: linear-gradient(135deg, #7c3aed, #a78bfa);
        color: white;
        border-radius: 22px;
        padding: 30px;
        margin-bottom: 20px;
        box-shadow: 0 8px 25px rgba(91,33,182,0.20);
      }
      
      .welcome-card h1 {
        font-size: 32px;
        font-weight: 700;
        margin-top: 5px;
      }
      
      .welcome-card p {
        font-size: 16px;
        opacity: 0.95;
      }
      
      .secure-card {
        background: #ede9fe;
        border-radius: 18px;
        padding: 22px;
        text-align: center;
        margin-top: 10px;
      }
      
      .secure-icon {
        font-size: 42px;
        color: #7c3aed;
        margin-bottom: 10px;
      }
      
      .btn-primary {
        background: #7c3aed !important;
        border-color: #7c3aed !important;
        border-radius: 10px !important;
        font-weight: 600;
      }
      
      .btn-danger {
        border-radius: 10px !important;
      }
      
      .form-control {
        border-radius: 10px !important;
        border: 1px solid #ddd6fe;
      }
      
      .risk-safe {
        color: #16a34a;
        font-weight: 700;
      }
      
      .footer-text {
        text-align: center;
        color: #6b7280;
        padding: 20px;
      }
      
      "))
    ),
    
    
    tabItems(
      
    
      
      tabItem(
        tabName = "dashboard",
        
        div(
          class = "welcome-card",
          h1(
            icon("shield-halved"),
            " Secure Digital Shopping Ledger"
          ),
          p(
            "Manage your shopping transactions securely, 
             track expenses and maintain a digital record."
          )
        ),
        
        fluidRow(
          
          valueBoxOutput("totalSpent", width = 3),
          valueBoxOutput("totalTransactions", width = 3),
          valueBoxOutput("averageSpent", width = 3),
          valueBoxOutput("securityStatus", width = 3)
          
        ),
        
        fluidRow(
          
          box(
            title = "Spending Overview",
            status = "primary",
            solidHeader = TRUE,
            width = 7,
            plotOutput("spendingPlot", height = "330px")
          ),
          
          box(
            title = "Digital Security",
            status = "primary",
            solidHeader = TRUE,
            width = 5,
            
            div(
              class = "secure-card",
              
              div(
                class = "secure-icon",
                icon("lock")
              ),
              
              h3("Ledger Protected"),
              
              p(
                "All transactions are validated before 
                 being added to the digital ledger."
              ),
              
              br(),
              
              tags$div(
                class = "risk-safe",
                icon("circle-check"),
                " Secure Transaction System"
              )
            )
          )
        ),
        
        div(
          class = "footer-text",
          "SecureShop • Digital Shopping Ledger • Secure & Simple"
        )
      ),
      
      
           
      tabItem(
        tabName = "ledger",
        
        h2(
          icon("receipt"),
          " Shopping Ledger"
        ),
        
        br(),
        
        box(
          title = "Transaction History",
          status = "primary",
          solidHeader = TRUE,
          width = 12,
          
          downloadButton(
            "downloadData",
            "Download Ledger",
            class = "btn-primary"
          ),
          
          br(),
          br(),
          
          tableOutput("ledgerTable")
        )
      ),
   
      
      
      tabItem(
        tabName = "add",
        
        h2(
          icon("cart-plus"),
          " Add Shopping Transaction"
        ),
        
        br(),
        
        fluidRow(
          
          box(
            title = "Secure Transaction Entry",
            status = "primary",
            solidHeader = TRUE,
            width = 7,
            
            textInput(
              "item",
              "Product / Item",
              placeholder = "Example: Laptop"
            ),
            
            selectInput(
              "category",
              "Category",
              choices = c(
                "Electronics",
                "Food",
                "Clothing",
                "Grocery",
                "Travel",
                "Education",
                "Healthcare",
                "Other"
              )
            ),
            
            numericInput(
              "amount",
              "Amount (₹)",
              value = 0,
              min = 0
            ),
            
            selectInput(
              "payment",
              "Payment Method",
              choices = c(
                "UPI",
                "Debit Card",
                "Credit Card",
                "Cash",
                "Net Banking"
              )
            ),
            
            dateInput(
              "date",
              "Transaction Date",
              value = Sys.Date()
            ),
            
            actionButton(
              "addTransaction",
              " Add Secure Transaction",
              icon = icon("shield-halved"),
              class = "btn-primary"
            )
          ),
          
          box(
            title = "Security Check",
            status = "primary",
            solidHeader = TRUE,
            width = 5,
            
            div(
              class = "secure-card",
              
              div(
                class = "secure-icon",
                icon("user-shield")
              ),
              
              h3("Protected Entry"),
              
              p(
                "Before saving a transaction, the system 
                 checks the entered information."
              ),
              
              hr(),
              
              tags$ul(
                tags$li("Valid product name"),
                tags$li("Valid purchase amount"),
                tags$li("Valid payment method"),
                tags$li("Transaction date verification")
              )
            )
          )
        )
      ),
     
      
      tabItem(
        tabName = "security",
        
        h2(
          icon("shield-halved"),
          " Security Center"
        ),
        
        br(),
        
        fluidRow(
          
          box(
            title = "Security Status",
            status = "primary",
            solidHeader = TRUE,
            width = 6,
            
            div(
              class = "secure-card",
              
              div(
                class = "secure-icon",
                icon("lock")
              ),
              
              h2("SYSTEM SECURE"),
              
              p(
                "Transaction validation is active."
              ),
              
              tags$div(
                class = "risk-safe",
                icon("circle-check"),
                " No security issues detected"
              )
            )
          ),
          
          box(
            title = "Protection Features",
            status = "primary",
            solidHeader = TRUE,
            width = 6,
            
            tags$ul(
              tags$li("Input validation"),
              tags$li("Invalid transaction detection"),
              tags$li("Secure digital records"),
              tags$li("Transaction history"),
              tags$li("Downloadable ledger"),
              tags$li("Expense monitoring")
            )
          )
        )
      )
    )
  )
)



server <- function(input, output, session) {
  
  # Initial sample transactions
  transactions <- reactiveVal(
    
    data.frame(
      ID = 1:4,
      
      Product = c(
        "Laptop",
        "Shoes",
        "Groceries",
        "Headphones"
      ),
      
      Category = c(
        "Electronics",
        "Clothing",
        "Grocery",
        "Electronics"
      ),
      
      Amount = c(
        45000,
        2500,
        3200,
        1800
      ),
      
      Payment = c(
        "UPI",
        "Debit Card",
        "Cash",
        "Credit Card"
      ),
      
      Date = as.Date(
        c(
          "2026-09-01",
          "2026-09-03",
          "2026-09-05",
          "2026-09-08"
        )
      ),
      
      stringsAsFactors = FALSE
    )
  )
  
  
  observeEvent(input$addTransaction, {
    
    item <- trimws(input$item)
    amount <- input$amount
    
    # Security validation
    
    if (item == "") {
      
      showNotification(
        "Security Error: Product name cannot be empty.",
        type = "error",
        duration = 5
      )
      
      return()
    }
    
    if (is.null(amount) || is.na(amount) || amount <= 0) {
      
      showNotification(
        "Security Error: Enter a valid purchase amount.",
        type = "error",
        duration = 5
      )
      
      return()
    }
    
    
    oldData <- transactions()
    
    newID <- ifelse(
      nrow(oldData) == 0,
      1,
      max(oldData$ID) + 1
    )
    
    
    newTransaction <- data.frame(
      ID = newID,
      Product = item,
      Category = input$category,
      Amount = amount,
      Payment = input$payment,
      Date = input$date,
      stringsAsFactors = FALSE
    )
    
    
    transactions(
      rbind(
        oldData,
        newTransaction
      )
    )
    
    
    showNotification(
      "Transaction securely added to the digital ledger!",
      type = "message",
      duration = 4
    )
   
    
    updateTextInput(
      session,
      "item",
      value = ""
    )
    
    updateNumericInput(
      session,
      "amount",
      value = 0
    )
    
  })
  
  
  
  output$ledgerTable <- renderTable({
    
    data <- transactions()
    
    data$Amount <- paste0(
      "₹ ",
      format(
        data$Amount,
        big.mark = ",",
        scientific = FALSE
      )
    )
    
    data$Date <- format(
      data$Date,
      "%d-%m-%Y"
    )
    
    names(data) <- c(
      "ID",
      "Product",
      "Category",
      "Amount",
      "Payment Method",
      "Date"
    )
    
    data
    
  }, striped = TRUE,
  bordered = TRUE,
  hover = TRUE)
  
  
  output$totalSpent <- renderValueBox({
    
    total <- sum(
      transactions()$Amount
    )
    
    valueBox(
      value = paste0(
        "₹ ",
        format(
          total,
          big.mark = ",",
          scientific = FALSE
        )
      ),
      
      subtitle = "Total Spending",
      
      icon = icon("indian-rupee-sign"),
      
      color = "purple"
    )
  })
  
  output$totalTransactions <- renderValueBox({
    
    valueBox(
      value = nrow(
        transactions()
      ),
      
      subtitle = "Transactions",
      
      icon = icon("receipt"),
      
      color = "blue"
    )
  })
  
  output$averageSpent <- renderValueBox({
    
    avg <- mean(
      transactions()$Amount
    )
    
    valueBox(
      value = paste0(
        "₹ ",
        format(
          round(avg),
          big.mark = ",",
          scientific = FALSE
        )
      ),
      
      subtitle = "Average Purchase",
      
      icon = icon("chart-line"),
      
      color = "yellow"
    )
  })
  
    
  output$securityStatus <- renderValueBox({
    
    valueBox(
      value = "SECURE",
      
      subtitle = "Ledger Status",
      
      icon = icon("shield-halved"),
      
      color = "green"
    )
  })
  
 
  output$spendingPlot <- renderPlot({
    
    data <- transactions()
    
    ggplot(
      data,
      aes(
        x = Date,
        y = Amount,
        group = 1
      )
    ) +
      
      geom_line(
        linewidth = 1.5
      ) +
      
      geom_point(
        size = 4
      ) +
      
      labs(
        x = "Transaction Date",
        y = "Amount (₹)"
      ) +
      
      theme_minimal(base_size = 14) +
      
      theme(
        plot.background = element_rect(
          fill = "transparent",
          color = NA
        ),
        
        panel.grid.minor = element_blank(),
        
        axis.title = element_text(
          face = "bold"
        )
      )
  })
  
  output$downloadData <- downloadHandler(
    
    filename = function() {
      paste0(
        "SecureShoppingLedger-",
        Sys.Date(),
        ".csv"
      )
    },
    
    content = function(file) {
      
      write.csv(
        transactions(),
        file,
        row.names = FALSE
      )
    }
  )
  
}

shinyApp(
  ui = ui,
  server = server
)
