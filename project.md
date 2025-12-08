<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>

## Predicting PV Power Generation from Weather Conditions


## Introduction 

Solar photovoltaic power is one of the fastest-growing sources of renewable energy, but its output varies significantly with atmospheric conditions. Predicting how much power a PV plant will produce at any given moment is an important challenge for grid reliability and energy planning becuase of weather variability. 

In this project, I use real operational data from a utility-scale solar plant and apply supervised machine learning techniques to model how environmental conditions influence AC power output. The dataset comes from the Solar Power Generation Data collection on Kaggle. It includes inverter power measurements and weather sensor data from a plant in India. By training a regression model on measurements of irradiance, ambient temperature, and module temperature, I found the most important factors beghind solar generation and and how to prevent inverter clipping and thermal loss.

From the dataset, we find that solar irradiance is the primary driver of AC power output. Power increases rapidly, but the relationship is nonlinear. At higher irradiance, the power levels started to flatten which shows the technological limits of the panels. Temperature also plays a big role, because at higher temperatures, the output is reduced due to decreased cell efficiency. The model can predict inverter clipping events and overall defficiency. With that being said, a simple linear regression model does a good job showing the general relationship between these factors. 

## Data

Here is an overview of the dataset, how it was obtained and the preprocessing steps taken, with some plots!

Because PV modules and inverters respond to irradiance with a physical delay, rapid changes in sunlight do not produce instantaneous changes in AC power. This causes noise in the scatter plots even after filtering. Despite this, the overall nonlinear trends are still clear.

![](assets/IMG/datapenguin.png){: width="500" }

*Figure 1: Here is a caption for my diagram. This one shows a pengiun [1].*

## Modelling

Here are some more details about the machine learning approach, and why this was deemed appropriate for the dataset. 

<p>
When \(a \ne 0\), there are two solutions to \(ax^2 + bx + c = 0\) and they are
  \[x = {-b \pm \sqrt{b^2-4ac} \over 2a}.\]
</p>

The model might involve optimizing some quantity. You can include snippets of code if it is helpful to explain things.

```python
from sklearn.ensemble import ExtraTreesClassifier
from sklearn.datasets import make_classification
X, y = make_classification(n_features=4, random_state=0)
clf = ExtraTreesClassifier(n_estimators=100, random_state=0)
clf.fit(X, y)
clf.predict([[0, 0, 0, 0]])
```

This is how the method was developed.

## Results

Figure X shows... [description of Figure X].

## Discussion

The graph clearly demonstrates that solar irradiance fluctuates rapidly due to clouds and atmospheric variability, while AC power follows a much smoother curve because the PV system responds with thermal and electrical inertia. Power rises after sunrise, peaks midday, and declines toward sunset, with a visible plateau during high-irradiance periods indicating inverter clipping. Both irradiance and AC power correctly drop to zero at night. Overall, the figure highlights that irradiance is the main driver of production, but the relationship is not instantaneous or linear due to system limits and physical lag processes.

## Conclusion

Here is a brief summary. From this work, the following conclusions can be made:
* first conclusion
* second conclusion

Here is how this work could be developed further in a future project.

## References
[1] DALL-E 3

[back](./)

