import streamlit as st

st.set_page_config(page_title="SupportAI", layout="wide")


if "show_reset" not in st.session_state:
    st.session_state.show_reset = False

st.markdown("""
<style>
body { background-color: #f6f7fb; }

.header {
    background: linear-gradient(90deg, #5b4bdb, #8b5cf6);
    padding: 50px;
    border-radius: 20px;
    color: white;
    text-align: center;
    margin-bottom: 30px;
}

.card {
    background-color: white;
    padding: 30px;
    border-radius: 15px;
    box-shadow: 0px 10px 30px rgba(0,0,0,0.08);
}

.stButton button {
    background: linear-gradient(90deg, #5b4bdb, #8b5cf6);
    color: white;
    border-radius: 8px;
    padding: 10px 20px;
}
</style>
""", unsafe_allow_html=True)

st.markdown("""
<div class="header">
    <h1>SupportAI</h1>
    <p>Intelligent Knowledge Management Platform</p>
</div>
""", unsafe_allow_html=True)

tab1, tab2 = st.tabs(["🔐 Sign In", "📝 Sign Up"])
with tab1:
    col1, col2, col3 = st.columns([1, 2, 1])
    with col2:
        st.markdown('<div class="card">', unsafe_allow_html=True)
        st.subheader("Welcome Back")

        email = st.text_input(
            "Email",
            placeholder="Enter your email",
            key="login_email"
        )

        password = st.text_input(
            "Password",
            type="password",
            key="login_password"
        )

        if st.button("Sign In", key="login_btn"):
            st.success("Login successful (demo)")

        st.markdown("🔗 **Forgot password?**")

        if st.button("Reset Password", key="show_reset_btn"):
            st.session_state.show_reset = True

        st.markdown('</div>', unsafe_allow_html=True)

if st.session_state.show_reset:
    st.markdown("---")
    col1, col2, col3 = st.columns([1, 2, 1])
    with col2:
        st.markdown('<div class="card">', unsafe_allow_html=True)
        st.subheader("Reset Password")

        reset_email = st.text_input(
            "Registered Email",
            key="reset_email"
        )

        new_pass = st.text_input(
            "New Password",
            type="password",
            key="reset_new_password"
        )

        if st.button("Send Reset Link", key="reset_btn"):
            st.success("Password reset email sent (demo)")
            st.session_state.show_reset = False

        st.markdown('</div>', unsafe_allow_html=True)

