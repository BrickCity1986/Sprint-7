import streamlit as st  
import pandas as pd
import plotly.express as px


import pandas as pd

# Read the csv files into separate pandas DataFrames
instacart_orders_df = pd.read_csv("/datasets/instacart_orders.csv")
instacart_orders_df.head()

products_df = pd.read_csv("/datasets/products.csv")
products_df.head()

aisles_df = pd.read_csv("/datasets/aisles.csv")
aisles_df.head()

departments_df = pd.read_csv("/datasets/departments.csv")
departments_df.head()

order_products_df = pd.read_csv("/datasets/order_products__path.csv")
order_products_df.head()


st.title('Instacart Data Analysis')

# Create a subheader
st.subheader("Data Overview")

# Create a histogram
st.subheader("Histogram")
hist_fig = px.histogram(instacart_orders_df, x="order_hour_of_day")
st.plotly_chart(hist_fig, use_container_width=True)

# Create a scatter plot
st.subheader("Scatter Plot")
scatter_fig = px.scatter(instacart_orders_df, x="order_hour_of_day", y="order_dow")  
st.plotly_chart(scatter_fig, use_container_width=True)

# Checkbox in the sidebar
show_histogram = st.sidebar.checkbox("Show Histogram")
if show_histogram:
    fig = px.histogram(instacart_orders_df, x="order_hour_of_day")  
    st.plotly_chart(fig)


