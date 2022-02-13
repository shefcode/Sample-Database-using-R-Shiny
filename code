library(shiny)
library(shinydashboard)
library(readxl)

# Read files
car_ds <- read_xlsx(path = "~/Documents/R Shiny/dataset/cars dataset.xlsx")
co2_ds <- read_xlsx(path = "~/Documents/R Shiny/dataset/CO2 dataset.xlsx")
dnase_ds <- read_xlsx(path = "~/Documents/R Shiny/dataset/DNase dataset.xlsx")
orange_ds <- read_xlsx(path = "~/Documents/R Shiny/dataset/Orange dataset.xlsx")

ui <- dashboardPage(
  skin = "green",
  dashboardHeader(title = "Sample Database",
                  titleWidth = 260),
  dashboardSidebar(
    width = 260,
    sidebarMenu(
      menuItem("Dashboard", tabName = "data", icon = icon("dashboard")),
      menuItem("Browse Table", tabName = "table", icon = icon("table"))
      )
  ),
  dashboardBody(
    tabItems(
      tabItem("data", fluidRow(box(width = 8, title = "Welcome to the Sample Database"))),
      tabItem("table", h1("Browse Table"),
              selectInput("table-list", "View Table", list("Car", "CO2", "DNase", "Orange")),
              fluidRow(box(width = 15, dataTableOutput("table")))
              )
      )
    )
)
server <- function(input, output) {
  datasetInput <- reactive({
    switch(input$table-list, "Car" = car_ds, "CO2" = co2_ds, "DNase" = dnase_ds, "Orange" = orange_ds)
  })
  }
shinyApp(ui, server)
