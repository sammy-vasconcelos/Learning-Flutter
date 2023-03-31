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
- Função que recebe função com paramentro
```dart
int executarVariasVezes(int quantidade, Function(String) fn, String valor){
  String textoCompleto = '';
  for (int i = 0; i < quantidade; i++){
    textoCompleto += fn(valor);
  }
  return textoCompleto.length;
}
main(){
  var meuPrint = (String valor) {
    print(valor);
    return valor;
  };
  var tamanho = executarVariasVezes(10, meuPrint, "Muito legal");
  print(tamanho);
}
```
- Função que retorna uma função poder acelerar o processamento das operações:
```
funcaoFora(p1){
  //setenca 1
  //setenca 2
  //setenca 3
  return (p2){
    //setenca 1
    //setenca 2
  }
}
```
Considerando que a funçãoFora demora 10s para processar e a segunda demora 1s,
chamar a funçãoFora 3x assim: 
```
funcaoFora(3)(11)
```
vai demorar 33s.
Fazer a função: 
```
var funcaoParam = funcaoFora(3)
```
 e
chamar 3x essa variavel: funcaoParam(11) vai demorar apenas 13s

![](https://media.tenor.com/bQuWIFsZWEgAAAAM/thurston-waffles-meow.gif)
<br />
<br />
# Filter
```dart
main() {
  var notas = [8.2, 7.1, 6.2, 4.4, 8.8, 9.1, 5.1, 10.0, 9.5, 9.0];
  // fazer funçoes como essa é bom por que elas podem ser reutilizadas utilizando outras listas
  var notasBoasFn = (double nota) => nota >= 7 && nota < 9;
  var notasMuitoBoasFn = (double nota) => nota >= 9;
  //o where faz um teste para saber se  o elemento vai fazer parte ou não do resultado final
  var notasBoas = notas.where(notasBoasFn);
  var notasMuitoBoas = notas.where(notasMuitoBoasFn);

  print("notas normais: ${notas}");
  print("Notas boas: ${notasBoas}");
  print("Notas MUITO boas: ${notasMuitoBoas}");
}
```
- exemplo com Generics: 
```dart
List<COISA> filtrar<COISA>(List<COISA> lista, bool Function(COISA) fn){
  List<COISA> listaFiltrada = [];
  for(COISA elemento in lista){
    if(fn(elemento)){
      listaFiltrada.add(elemento);
    }
  }
  return listaFiltrada;
}
main(){
  var nomes = ["ana", "benedito", "Edmundo", "bea", "João"];
  var nomesGrandes = (String nomes) => nomes.length > 4;
  print(filtrar(nomes, nomesGrandes));
}
```
