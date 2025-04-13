import re
import streamlit as st

# Page styling
st.set_page_config(page_title="Password Strength Checker By Zeba Khan", page_icon="🔐", layout="centered")

# Custom CSS
st.markdown("""
    <style>
        .main {
            text-align: center;
        }
        div.stButton > button {
            width: 50%;
            margin: auto;
            display: block;
            background-color: #4CAF50;
            color: white;
            font-size: 18px;
            border: none;
            border-radius: 8px;
            padding: 10px;
            transition: background-color 0.3s ease;
        }
        div.stButton > button:hover {
            background-color: #45a049;
        }
        .stTextInput {
            width: 60% !important;
            margin: auto;
        }
    </style>
""", unsafe_allow_html=True)

# Page title and description
st.title("🔐 Password Strength Generator")
st.write("This page checks the strength of your password and provides suggestions to make it stronger.🔍")

# Function to check password strength
def check_password_strength(password):
    score = 0
    feedback = []

    if len(password) >= 8:
        score += 1
    else:
        feedback.append("❌ Password should be **at least 8 characters long**.")

    if re.search(r"[A-Z]", password) and re.search(r"[a-z]", password):
        score += 1
    else:
        feedback.append("❌ Password should contain **both uppercase [A-Z] and lowercase (a-z) letters**.")

    if re.search(r"\d", password):
        score += 1
    else:
        feedback.append("❌ Password should contain **at least one digit [0-9]**.")

    if re.search(r"[!@#$%^&*(),.?\":|<>]", password):
        score += 1
    else:
        feedback.append("❌ Include **at least one special character (!@#$%^&*(),.?\":|<>)**.")

    # Display password strength results
    if score == 4:
        st.success("✅ Password is **strong**!")
    elif score == 3:
        st.warning("⚠️ Password is **moderate**. Consider adding more complexity.")
    else:
        st.error("❌ Password is **very weak**. Follow the suggestions below to strengthen it.")

    # Display feedback
    if feedback:
        with st.expander("🔎 **Improve Your Password**"):
            for item in feedback:
                st.write(item)

# Input field for password
password = st.text_input("Enter your password: ", type="password", help="Ensure your password is strong 🔐")

# Button to check password strength
if st.button("Check Password Strength"):
    if password:
        check_password_strength(password)
    else:
        st.warning("⚠️ Please enter a password to check its strength.")
