# Calculator-App

import React, { useState } from 'react';
import { StyleSheet, Text, View, TouchableOpacity } from 'react-native';

const Calculator = () => {
  const [displayValue, setDisplayValue] = useState('0');
  const [operator, setOperator] = useState(null);
  const [firstOperand, setFirstOperand] = useState(null);

  const handleNumberPress = (number) => {
    if (displayValue === '0') {
      setDisplayValue(number.toString());
    } else {
      setDisplayValue(displayValue + number.toString());
    }
  };

  const handleOperatorPress = (op) => {
    setOperator(op);
    setFirstOperand(parseFloat(displayValue));
    setDisplayValue('0');
  };

  const handleEqualsPress = () => {
    const secondOperand = parseFloat(displayValue);
    let result;

    switch (operator) {
      case '+':
        result = firstOperand + secondOperand;
        break;
      case '-':
        result = firstOperand - secondOperand;
        break;
      case '*':
        result = firstOperand * secondOperand;
        break;
      case '/':
        result = firstOperand / secondOperand;
        break;
      default:
        result = displayValue;
    }

    setDisplayValue(result.toString());
    setOperator(null);
    setFirstOperand(null);
  };

  const handleClearPress = () => {
    setDisplayValue('0');
    setOperator(null);
    setFirstOperand(null);
  };

  return (
    <View style={styles.container}>
      <Text style={styles.display}>{displayValue}</Text>
      <View style={styles.buttons}>
        <TouchableOpacity onPress={() => handleNumberPress(1)} style={styles.button}>
          <Text style={styles.buttonText}>1</Text>
        </TouchableOpacity>
        <TouchableOpacity onPress={() => handleNumberPress(2)} style={styles.button}>
          <Text style={styles.buttonText}>2</Text>
        </TouchableOpacity>
        <TouchableOpacity onPress={() => handleNumberPress(3)} style={styles.button}>
          <Text style={styles.buttonText}>3</Text>
        </TouchableOpacity>
        <TouchableOpacity onPress={() => handleOperatorPress('+')} style={styles.button}>
          <Text style={styles.buttonText}>+</Text>
        </TouchableOpacity>
        <TouchableOpacity onPress={() => handleNumberPress(4)} style={styles.button}>
          <Text style={styles.buttonText}>4</Text>
        </TouchableOpacity>
        <TouchableOpacity onPress={() => handleNumberPress(5)} style={styles.button}>
          <Text style={styles.buttonText}>5</Text>
        </TouchableOpacity>
        <TouchableOpacity onPress={() => handleNumberPress(6)} style={styles.button}>
          <Text style={styles.buttonText}>6</Text>
        </TouchableOpacity>
        <TouchableOpacity onPress={() => handleOperatorPress('-')} style={styles.button}>
          <Text style={styles.buttonText}>-</Text>
        </TouchableOpacity>
        <TouchableOpacity onPress={() => handleNumberPress(7)} style={styles.button}>
          <Text style={styles.buttonText}>7</Text>
        </TouchableOpacity>
        <TouchableOpacity onPress={() => handleNumberPress(8)} style={styles.button}>
          <Text style={styles.buttonText}>8</Text>
        </TouchableOpacity>
        <TouchableOpacity onPress={() => handleNumberPress(9)} style={styles.button}>
          <Text style={styles.buttonText}>9</Text>
        </TouchableOpacity>
        <TouchableOpacity onPress={() => handleOperatorPress('*')} style={styles.button}>
          <Text style={styles.buttonText}>*</Text>
        </TouchableOpacity>
        <TouchableOpacity onPress={() => handleNumberPress(0)} style={styles.button}>
          <Text style={styles.buttonText}>0</Text>
        </TouchableOpacity>
        <TouchableOpacity onPress={() => handleEqualsPress()} style={styles.button}>
          <Text style={styles.buttonText}>=</Text>
        </TouchableOpacity>
        <TouchableOpacity onPress={() => handleClearPress()} style={styles.button}>
          <Text style={styles.buttonText}>C</Text>
        </TouchableOpacity>
        <TouchableOpacity onPress={() => handleOperatorPress('/')} style={styles.button}>
          <Text style={styles.buttonText}>/</Text>
        </TouchableOpacity>
      </View>
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
  },
  display: {
    fontSize: 36,
    marginBottom: 20,
  },
  buttons: {
    flexDirection: 'row',
    flexWrap: 'wrap',
  },
  button: {
    width: '25%',
    aspectRatio: 1,
    alignItems: 'center',
    justifyContent: 'center',
    borderWidth: 1,
    borderColor: 'gray',
  },
  buttonText: {
    fontSize: 24,
  },
});

export default Calculator;
