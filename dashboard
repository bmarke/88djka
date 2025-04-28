import streamlit as st
import pandas as pd

# Title
st.title("Audit Evidence Tracker")

# Load the CSV
data = pd.read_csv("evidence.csv")

# Show the raw table
st.subheader("Evidence Status Table")
st.dataframe(data)

# Calculate simple KPIs
passed = data[data['status'] == 'Pass'].shape[0]
failed = data[data['status'] == 'Fail'].shape[0]

# Display KPIs
col1, col2 = st.columns(2)
col1.metric("✅ Passed Controls", passed)
col2.metric("❌ Failed Controls", failed)

# Add a filter by Owner
st.subheader("Filter by Owner")
owners = data['owner'].unique()
selected_owner = st.selectbox("Select Owner", ["All"] + list(owners))

if selected_owner != "All":
    filtered_data = data[data['owner'] == selected_owner]
    st.dataframe(filtered_data)
else:
    st.dataframe(data)

# Add a bar chart for pass/fail
st.subheader("Control Status Chart")
status_counts = data['status'].value_counts()
st.bar_chart(status_counts)
