# Learning-Flutter
anotações dos meus estudos em Flutter :)

## Funções

Uma função `void` se refere a uma função que não retorna nada.

```dart
void somaNum(int a, int b){
  print(a + b);
}
```
- retornar os dados de uma função permite que esses dados possam ser usados em alguma situação desejada.
- colocar um parâmetro deafult vai fazer com que o tipo dele seja dinâmico, ex: 
```dart
exDinamico(a, b){
  return print( a.toString() + b.toString());
}
```
- o parâmetro é opcional quando está entre colchetes ou entre chaves, um valor precisa ser atribuido para que tenha um valor padrão caso o valor não seja informado, ex: 
```dart
paramOpcional1([int a = 10]){
  return a;
}

//ou

paramOpcional2({int a = 10, int b = 5}){
  return a
}
```
