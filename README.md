# MATLAB Onramp: Technical Core Concepts & Syntax Reference

## 1. Mathematical Commands & Workspace Management
*   **Dynamic Type Environment:** MATLAB allocates variable memory instantly upon assignment. It uses the single `=` operator. It requires no explicit data type declarations.
*   **Console Output Suppression:** Standard operations print results to the screen by default. Appending a semicolon `;` terminates expressions quietly. This saves the variable to the **Workspace** while suppressing console feedback.
*   **Native Engine Constants:** High-precision defaults are built into the language. You can use terms like `pi` ($\approx 3.14159$) immediately.

```matlab
% Variable assignment with console output visible
variableName = 10 

% Variable assignment with output suppressed via semicolon
x = 5; 

% Basic algebraic composition utilizing the native 'pi' constant
radius = 3;
area = pi * radius^2;
```

---

## 2. Array Generation & Vectorization Foundations
*   **Matrix Laboratory Architecture:** The language treats all data structures as multi-dimensional matrices. A single scalar value is a $1 \times 1$ matrix.
*   **Manual Array Construction:** Separate elements with spaces or commas `,` to build columns for a **row vector**. Use a semicolon `;` to break to the next row for a **column vector**.
*   **Automated Sequence Generation:** The colon operator `:` generates long, evenly spaced number sequences. It uses the syntax `Start:Increment:End`. The step increment defaults to `1` if omitted.
*   **Pre-allocated Memory Functions:** Built-in structural functions optimize memory allocation. Commands like `zeros()` and `ones()` quickly pre-populate matrices of any size.

```matlab
% Row Vector creation (1x3 Array) using spaces
rowVec = [1 2 3]; 

% Column Vector creation (3x1 Array) using semicolons
colVec = [4; 5; 6]; 

% Matrix composition (2x3 Array) combining row and column mechanics
matrixA = [1 2 3; 4 5 6]; 

% Linearly spaced sequence (Integers 1 through 10, default step = 1)
seqDefault = 1:10; 

% Stepped sequence specifying a precise fractional increment (0 to 2 by 0.5)
seqStep = 0:0.5:2; 

% Memory pre-allocation for a 3-row, 4-column matrix of zeros
allZeros = zeros(3, 4);  

% Memory pre-allocation for a 2-row, 5-column matrix of ones
allOnes = ones(2, 5);   
```

---

## 3. Dimensional Indexing & Matrix Modification
*   **1-Based Index System:** Array index references begin at position `1`. They do not start at position `0`.
*   **Coordinate Pointer System:** Locate specific cells inside a 2D matrix using `(row, column)` notation.
*   **Dynamic Bounds Referencing:** The `end` keyword automatically calculates the final index value of a specific dimension.
*   **Matrix Slicing Wildcard:** A single colon `:` serves as a full-dimension placeholder. This technique extracts or copies rows and columns without changing the original matrix.

```matlab
% Extract the specific value located at Row 2, Column 3
element = matrixA(2, 3); 

% Mutate data by overwriting the value at Row 1, Column 2
matrixA(1, 2) = 10; 

% Dynamic index mapping using the 'end' keyword
lastElement = rowVec(end);

% Extract a subset from the 2nd element to the absolute end
subVector = rowVec(2:end); 

% Column slicing: Extract ALL rows within column 2 (results in a column vector)
secondColumn = matrixA(:, 2);  

% Row slicing: Extract ALL columns within row 1 (results in a row vector)
firstRow = matrixA(1, :);  
```

---

## 4. Matrix Mathematics & Element-Wise Vectorization
*   **Linear Algebra Operators:** Standard math symbols like `*`, `/`, and `^` enforce formal matrix transformation rules. Multiplying two matrices requires their inner dimensions to match perfectly.
*   **Position-Specific Vectorization:** Place a period `.` before operators (`.*`, `./`, `.^`) to change calculation behavior. These **element-wise dot operators** calculate computations coordinate-by-coordinate. Both data arrays must share identical dimensions.

```matlab
% Scalar modification (Broadcasting a value across a whole array)
scaledMatrix = matrixA * 2; 

% Linear Algebra Matrix Multiplication 
% Requires inner dimensions to match: e.g., (2x3 matrix) * (3x2 matrix)
matrixProduct = matrixA * matrixB; 

% Element-Wise Multiplication (Requires arrays of identical dimensions)
% Multiplies position (1,1) by position (1,1), position (1,2) by (1,2), etc.
elementProduct = matrixA .* matrixMatrix; 

% Element-Wise Exponentiation (Squares every single number inside the matrix)
squaredElements = matrixA .^ 2; 
```

---

## 5. Function Execution & Parameter Unpacking
*   **Functional Data Processing:** Functions accept inputs inside parentheses and calculate solutions.
*   **Multi-Variable Return Arrays:** Functions often return multiple distinct outputs. You must catch these values using a comma-separated list inside square brackets `[ ]` on the left side of your equation. This unpacks properties like values and index positions simultaneously.

```matlab
% Execute a single-input, single-output mathematical function
rootVal = sqrt(10); 

% Unpack the total rows and columns of a matrix into separate variables
[numRows, numCols] = size(matrixA); 

% Extract both the highest number and its index position from an array
[maximumValue, linearIndex] = max(rowVec); 
```

---

## 6. Data Visualization & Graphic Layout Design
*   **2D Grid Mapping:** The basic `plot(x, y)` command transforms vector arrays into visual charts.
*   **Property Code Specification:** Short text strings quickly customize line colors, marker shapes, and line patterns.
*   **Canvas Grid Persistence:** New plot commands overwrite active figures by default. Lock the active graph using `hold on` to layer multiple datasets. Release the canvas lock using `hold off`.

```matlab
% Generate a basic continuous line graph
plot(x, y); 

% Create a styled line: 'r' = Red, '--' = Dashed Line, 'o' = Circle Markers
plot(x, y, 'r--o'); 

% Freeze the current canvas to allow multi-line overlaying
hold on;      
plot(x, z, 'b:'); % Overlays a blue ('b'), dotted (':') line on the same axis
hold off;     % Releases the canvas lock so the next plot command resets the view

% Apply descriptive structural annotations to the active figure
title('Velocity Profile vs. Time');
xlabel('Elapsed Time (seconds)');
ylabel('Velocity (m/s)');
legend('Sensor Alpha', 'Sensor Beta');
```

---

## 7. Data Table Ingestion & Logical Index Filtering
*   **Tabular Data Containers:** Imported spreadsheets are organized into a structured layout called a **Table**.
*   **Dot-Notation Variable Isolation:** Isolate individual column vectors using the `tableName.ColumnName` format.
*   **Binary Mask Generation:** Relational comparison operators (`<`, `>`, `==`, `~=`) evaluate conditions. They return a **logical array** containing only binary flags (`1` for True, `0` for False).
*   **Logical Index Extraction:** Pass the binary mask array back into the original dataset. MATLAB filters out all `0` entries, leaving only matching values.

```matlab
% Extract a specific column vector from an imported data table
timeVector = sensorData.Time; 

% Evaluate a condition to generate a binary logical mask (1s and 0s)
mask = timeVector > 15.5; 

% Apply logical indexing to filter out only the elements that match the condition
filteredData = timeVector(mask); 
```

---

## 8. Programmatic Control Loops & Conditional Branching
*   **Sequential Decision Branching:** An `if/elseif/else` block tests data conditions sequentially. The engine executes only the pathway that evaluates to true.
*   **Definite Automation Cycles:** A `for` loop uses a counting index to repeat code blocks a predetermined number of times.

```matlab
% Evaluate data values to execute specific conditional branches
if threshold > 100
    status = "Critical Alert";
elseif threshold > 75
    status = "Warning State";
else
    status = "Normal Operation";
end

% Automate a repetitive task exactly 10 times using a 'for' loop
for index = 1:10
    % Calculate and save data step-by-step using the current loop index
    results(index) = computeCoreMetrics(index);
end
```
