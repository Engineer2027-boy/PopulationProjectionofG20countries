# basic flask layout will work on it more
from flask import Flask, render_template, request
import pandas as pd
import numpy as np
import plotly.io as pio
import plotly.graph_objects as go

app = Flask(__name__)


Index = ['USA', 'China', 'India', 'Japan', 'SouthKorea', 'Russia', 'Canada', 'Indonesia', 'Argentina', 'Germany',
         'France', 'UK', 'SaudiArabia', 'Brazil', 'Mexico', 'SouthAfrica', 'Italy', 'Turkey', 'Australia']


file = pd.read_excel("C:\\Users\\AYUSH ADITYA\\Desktop\\Data Science Documents\\Demographics_of_G20_Nations.xlsx",
                     sheet_name="Sheet3")

year_start = [1.862, 1.5697, 3.58, 1.5, 1.3423, 2, 1.89, 2.41, 1.81, 2.17, 1.92, 1.68, 4.81, 2.4183, 2.72, 2.61,
              1.22, 2.1, 1.8]


@app.route("/")
def home():
    return render_template("homepage.html")


@app.route("/p", methods=["GET", "POST"])
def population_projection():
    selected_country = None
    graph_html = None
    if request.method == "POST":
        selected_year = int(request.form.get("year"))
        selected_country = request.form.get("country")
        if selected_country in Index:
            index = 0
            selected_country_f = selected_country + "_Fertility"
            fertility = file[selected_country_f].to_numpy()
            goal = year_start[Index.index(selected_country)]
            for i in range(len(fertility)):
                if fertility[i] == goal:
                    index = i
                    break

            column = selected_country + "_Population"

            # Extract data
            years = file["Year"][index:].to_numpy()
            population = file[column][index:].to_numpy()
            years1 = file["Year"].to_numpy()
            population1 = file[column].to_numpy()
            # Filter out NaNs and get data up to 2024
            mask = (~np.isnan(population)) & (years <= 2024)
            years = years[mask]
            population = population[mask]
            # Fit 2nd-degree polynomial
            X = np.vstack([years ** 2, years, np.ones_like(years)]).T
            Y = population.reshape(-1, 1)
            beta = np.linalg.solve(X.T @ X, X.T @ Y).flatten()
            a, b, c = beta
            # Create ranges for plotting
            historical_years = years1[years1 <= 2024]
            historical_pop = population1[years1 <= 2024]
            projection_years = np.arange(2025, selected_year+1)
            projection_pop = a * projection_years ** 2 + b * projection_years + c
            # Plot
            # Create Plotly figure
            fig = go.Figure()

            # Historical data
            fig.add_trace(go.Scatter(
                x=historical_years,
                y=historical_pop,
                mode='lines+markers',
                name='Actual Data',
                hovertemplate='Year: %{x}<br>Population: %{y:.2f}'
            ))

            # Projection data
            fig.add_trace(go.Scatter(
                x=projection_years,
                y=projection_pop,
                mode='lines+markers',
                line=dict(dash='dash'),
                name='Projection',
                hovertemplate='Year: %{x}<br>Population: %{y:.2f}'
            ))

            # Transition marker at 2024
            transition_point = a * 2024 ** 2 + b * 2024 + c
            fig.add_trace(go.Scatter(
                x=[2024],
                y=[transition_point],
                mode='markers',
                marker=dict(color='green', size=10),
                name='2024 Transition',
                hovertemplate='Year: 2024<br>Population: %{y:.2f}'
            ))

            fig.update_layout(
                title=f"Population Projection for {selected_country}",
                xaxis_title='Year',
                yaxis_title='Population (millions)',
                hovermode='x unified',
                template='plotly_white',
                height=600
            )

            # Convert to HTML string
            graph_html = pio.to_html(fig, full_html=False)

    return render_template("population_projection.html", graph_html=graph_html, countries=Index, selected_country=selected_country)


@app.route('/m')
def methodology():
    return render_template("methodology.html")


if __name__ == "__main__":
    app.run(debug=True)


