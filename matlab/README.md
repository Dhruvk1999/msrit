# MATLAB Cheatsheet

## Basic Setup

```matlab
% Clear command window and workspace
clc; clear; close all;

%% <- This creates a code section
% Section 1

%% <- This creates code section
% Section 2
```

## Complex Numbers

```matlab
% Complex declaration
num = 3 + 4j; % a + bj
disp(num);

% Conjugate
disp(conj(num)); % 3 - 4j

% Magnitude
disp(abs(num)); % 5.00
```

## Array/List

```matlab
% Array/List declaration
list = [100, 10, 1];
rangeList = 1:5; % [1, 2, 3, 4, 5];

% Some useful list methods
disp(max(list)); % 100
disp(min(list)); % 1
disp(sort(list)); % [1, 10, 100]
disp(length(list)); % 3

% List multiplication
a = [1, 3, 6, 9];
b = [2, 4, 6, 8];
disp(times(a, b)); % [2, 12, 36, 72]
disp(a .* b); % alternative
disp(a * b'); % another alternative. b' -> transpose

% Map operations on array
disp(a .* 2); % mult every element by 2
disp(a ./ 2); % div every element by 2
disp(a .^ 2); % raise every element by pow(2)
disp(a + 2); % add 2 to every element
disp(a - 2); % sub 2 with every element
```

## Matrix Generation

```matlab
% Matrix declaration
x = [
    [1, 2, 3, 4];
    [5, 6, 7, 8];
    [9, 10, 11, 12];
    ];

x = [1:4; 5:8; 9:12];

% Useful methods
% ! In MATLAB, index starts at 1
disp(x(1, :)); % x[0] => get row
disp(x(:, 2)); % x -> Transpose -> x[0] => Get Column
disp(x(2:3, 2:3)); % get subset of matrix
disp(x(end, :)); % get last row

% Matrix generation
x = zeros(3, 2);
y = ones(2, 3);
z = eye(3); % identity matrix
disp(x); disp(y); disp(z);

% Append row(s) to matrix
x = ones(2, 2);
y = zeros(2, 2);
z = [x; y];
disp(z);

% Append col(s) to matrix
x = ones(2, 2);
y = zeros(2, 2);
z = [x y];
disp(z);

% Transpose of matrix
x = 1:3;
x = x';
disp(x);

% Random matrix
x = randi(100, 3); % (range, dimension)
disp(x);

% Special matrices
% `hilb(n)` `invhilb(n)` `magic(n)` `pascal(n)` `vander(n)`
```

## Matrix Manipulation

```matlab
% Shuffle and cols
x = [
    [1, 2, 3];
    [4, 5, 6];
    [7, 8, 0];
    ];

y = x([2, 1, 3], :); % shuffle rows
z = x(:, [3, 2, 1]); % shuffle cols
disp(y); disp(z);

% Flatten matrix
flat = x(:);
disp(flat);

% Remove row/col from matrix
x(2, :) = [];
disp(x);

% Selecting diagonal values
x = eye(3);
y = diag(x);
disp(y);

% Creating diagonal mask
x = [1:3; 4:6; 7:9] .* eye(3);
disp(x);
```

## Continuous Plot

```matlab
x = 0:pi / 10:2 * pi; % [0, 2pi] with increment of pi/100

y1 = 2 * cos(x);
y2 = cos(x);
y3 = cos(x) / 2;

plot(x, y1, ...
    x, y2, ...
    x, y3);

xlabel('0 \leq x \leq 2\pi');
ylabel('cos function')
legend('2.0 * cos(x)', '1.0 * cos(x)', '0.5 * cos(x)');
title('Effect of scalar on cos function');
axis([0, 2 * pi, -2, 2]); % this is auto
```

## Step Plot

```matlab
x = 0:pi / 10:2 * pi;
y1 = 2 * cos(x);

stem(x, y1);
```

## Subplot (Multiplot)

```matlab
x = 0:pi / 20:2 * pi;
y1 = 2 * cos(x);

subplot(1, 2, 1); % 1x2 grid. plot#1
plot(x, y1);
subplot(1, 2, 2); % 1x2 grid. plot#2
stem(x, y1);
```

## Problems

```matlab
% 1. Convert given expression into MATLAB expression
a = 5;
x = 2;
y = 8;

c = exp(-1 * a * x) * sin(x) + 50 * y^(1/3);
disp(c); % 100.0
```