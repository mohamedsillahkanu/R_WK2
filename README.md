# Load ggplot2 for visualization<br>
library(ggplot2)<br>
<br>
# Create a histogram of the 'Cases' column<br>
ggplot(malaria_data, aes(x = Cases)) +<br>
  geom_histogram(binwidth = 100, fill = "blue", color = "black") +<br>
  labs(title = "Distribution of Malaria Cases", x = "Cases", y = "Frequency")
                </code>
            </div>
            
            <div class="explanation">
                <h4>Explanation:</h4>
                <p>- <code>geom_histogram()</code> creates the histogram with custom bin width.<br>
                - <code>labs()</code> adds a title and labels to the axes.</p>
            </div>
            
            <hr>
            
            <h3>Exercise 3.2: Create a Scatter Plot</h3>
            <div class="r-code">
                <code>
# Create a scatter plot of 'Cases' vs 'Fatalities'<br>
ggplot(malaria_data, aes(x = Cases, y = Fatalities)) +<br>
  geom_point(color = "red") +<br>
  labs(title = "Malaria Cases vs Fatalities", x = "Cases", y = "Fatalities")
                </code>
            </div>
            
            <div class="explanation">
                <h4>Explanation:</h4>
                <p>- <code>geom_point()</code> creates a scatter plot. The points are colored red for visual distinction.<br>
                - <code>labs()</code> adds the title and axis labels.</p>
            </div>
            
            <hr>
            
            <h3>Exercise 3.3: Create a Boxplot</h3>
            <div class="r-code">
                <code>
# Create a boxplot of the 'Cases' column<br>
ggplot(malaria_data, aes(y = Cases)) +<br>
  geom_boxplot(fill = "lightgreen", color = "black") +<br>
  labs(title = "Boxplot of Malaria Cases", y = "Cases")
                </code>
            </div>
            
            <div class="explanation">
                <h4>Explanation:</h4>
                <p>- <code>geom_boxplot()</code> creates the boxplot. The box is filled with light green and outlined in black.<br>
                - <code>labs()</code> adds a title and y-axis label.</p>
            </div>
        </div>
        
        <div class="solution-section">
            <h2 id="sol-bonus2">4️⃣ Bonus Challenge: Automate Data Cleaning and Visualization</h2>
            
            <div class="r-code">
                <code>
# Ask the user for the file path<br>
file_path <- readline(prompt = "Enter the path to the CSV file: ")<br>
<br>
# Load the dataset<br>
library(readr)<br>
malaria_data <- read_csv(file_path)<br>
<br>
# Clean the data by handling missing values and outliers<br>
malaria_data$Cases[is.na(malaria_data$Cases)] <- mean(malaria_data$Cases, na.rm = TRUE)<br>
<br>
# Calculate Q1, Q3, and IQR for 'Cases' column<br>
Q1 <- quantile(malaria_data$Cases, 0.25, na.rm = TRUE)<br>
Q3 <- quantile(malaria_data$Cases, 0.75, na.rm = TRUE)<br>
IQR <- Q3 - Q1<br>
lower_bound <- Q1 - 1.5 * IQR<br>
upper_bound <- Q3 + 1.5 * IQR<br>
malaria_data <- malaria_data[malaria_data$Cases >= lower_bound & malaria_data$Cases <= upper_bound, ]<br>
<br>
# Create visualizations<br>
library(ggplot2)<br>
ggplot(malaria_data, aes(x = Cases)) +<br>
  geom_histogram(binwidth = 100, fill = "blue", color = "black") +<br>
  labs(title = "Distribution of Malaria Cases", x = "Cases", y = "Frequency")<br>
<br>
ggplot(malaria_data, aes(x = Cases, y = Fatalities)) +<br>
  geom_point(color = "red") +<br>
  labs(title = "Malaria Cases vs Fatalities", x = "Cases", y = "Fatalities")<br>
<br>
# Save the cleaned dataset to a new CSV file<br>
write_csv(malaria_data, "cleaned_malaria_data.csv")
                </code>
            </div>
            
            <div class="explanation">
                <h4>Explanation:</h4>
                <p>- The script asks the user for a file path and loads the dataset using <code>read_csv()</code>.<br>
                - It handles missing values and outliers (as described in previous steps).<br>
                - It creates the histogram and scatter plot for visualizations.<br>
                - Finally, it saves the cleaned dataset using <code>write_csv()</code>.</p>
            </div>
            
            <h3>💡 Additional Notes:</h3>
            <p>- Make sure to have the required libraries (<code>ggplot2</code>, <code>dplyr</code>, <code>readr</code>, etc.) installed before running the code.<br>
            - For the bonus challenge, ensure the path to the CSV file is correct, and if running on an interactive system like RStudio, input the file path properly.</p>
        </div>
        
        <hr>
        
        <h2>💡 What's Next?</h2>
        <p>✔ After completing these exercises, you will have learned how to clean and visualize malaria data.<br>
        ✔ In <strong>Week 3</strong>, we will dive deeper into advanced analysis techniques such as grouping, summarizing, and advanced plotting! 🚀</p>
    </div>
    
    <script src="script.js"></script>
</body>
</html>
