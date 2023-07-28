# Changes on Jul 28, 2023

## 1. Filtering occurrences

Before: `filtered_occurrences <- filtered_occurrences[filtered_occurrences$basisOfRecord != c("PRESERVED_SPECIMEN", "FOSSIL_SPECIMEN"), ]`

After: `filtered_occurrences <- filtered_occurrences[!(filtered_occurrences$basisOfRecord %in% c("PRESERVED_SPECIMEN", "FOSSIL_SPECIMEN")), ]`

Reason for Change:
The filtering of occurrences was updated to ensure that records with the basis of "PRESERVED_SPECIMEN" and "FOSSIL_SPECIMEN" are properly excluded. The previous code using `!=` operator was incorrect, so we now use the `%in%` operator to correctly exclude the specified basis of records.

## 2. Calculating correlation matrix

Before: `corr_matrix <- cor(suit_clim[2:16], method = "pearson")`

After: `corr_matrix <- cor(suit_clim[2:16], method = "pearson", use = "pairwise.complete.obs")`

Reason for Change:
The correlation calculation between variables in "suit_clim" data had missing values, which affected the accuracy of the results. By adding the "use = 'pairwise.complete.obs'" parameter, we now calculate the correlation using pairwise complete observations, ensuring a more accurate and meaningful correlation matrix.

## 3. Saving the correlation matrix

Added: `write.csv(corr_matrix, file = "./Training/corr_matrix.csv", row.names = FALSE)`

Reason for Change:
To make the correlation matrix accessible for further analysis and external use, we have added a step to export the matrix to a CSV file named "corr_matrix.csv" located in the "./Training" directory.

Please review and incorporate these changes into your project. If you have any questions or encounter any issues, feel free to reach out. Happy coding!
