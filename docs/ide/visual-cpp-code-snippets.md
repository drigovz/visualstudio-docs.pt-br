---
title: Snippets de código do Visual C++
ms.date: 11/04/2016
ms.topic: reference
author: corob-msft
ms.author: corob
manager: markl
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: db6ea1e233d32872322926a4d75b847ee6a49ba3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277834"
---
# <a name="visual-c-code-snippets"></a>Snippets de código do Visual C++

No Visual Studio, você pode usar snippets de código para adicionar código comumente usado nos seus arquivos de código do C++. Em geral, você pode usar os snippets de código de forma bem parecida com o C#, mas o conjunto de snippets de código padrão é diferente.

Você pode adicionar um snippet de código em um local específico no seu código (inserção) ou envolver algum código selecionado com um snippet de código.

## <a name="insert-a-code-snippet"></a>Inserir um snippet de código

Para inserir um trecho de código, abra um arquivo de código C++ (*. cpp* ou *. h*), clique em algum lugar dentro do arquivo e siga um destes procedimentos:

- Clique com o botão direito do mouse para obter o menu de contexto e selecione **Inserir Snippet**

- No menu **Editar / IntelliSense**, selecione **Inserir Snippet**

- Use as teclas de teclado: **Ctrl** + **K** + **X**

Você deve ver uma lista de opções que começam com **#if**. Ao selecionar **#if**, você verá o seguinte código adicionado ao arquivo:

```cpp
#if 0

#endif // 0
```

Em seguida, você pode substituir o **0** pela condição correta.

## <a name="use-a-code-snippet-to-surround-selected-code"></a>Usar um snippet de código para envolver o código selecionado

Para usar um snippet de código para envolver o código selecionado, selecione uma linha (ou várias linhas) e siga um destes procedimentos:

- Clique com o botão direito do mouse para obter o menu de contexto e selecione **Circundar com**

- No menu **Editar**  >  **IntelliSense** , selecione **surround com**

- Usando um teclado, pressione: **Ctrl** + **K** + **S**

Selecione **#if**. Você deverá ver algo como:

```cpp
#if 0
#include "pch.h"  // or whatever line you had selected
#endif // 0
```

Em seguida, você pode substituir o 0 pela condição correta.

## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>Onde posso encontrar uma lista completa dos snippets de código do C++?

Você pode encontrar a lista completa de snippets de código do C++ indo até o **Gerenciador de Snippets de Código** (no menu **Ferramentas**) e configurando a **Linguagem** para **Visual C++**. Na janela abaixo, expanda **Visual C++**. Você verá os nomes de todos os snippets de código do C++ em ordem alfabética.

Os nomes da maioria dos snippets de código são auto-explicativos, mas alguns nomes podem ser confusos.

## <a name="class-vs-classi"></a>Class versus classi

O snippet **class** fornece a definição de uma classe chamada `MyClass`, com o construtor e o destruidor padrão apropriado, em que as definições do construtor e do destruidor estão localizadas fora da classe:

```cpp
class MyClass
{
public:
    MyClass();
    ~MyClass();

private:

};

MyClass::MyClass()
{
}

MyClass::~MyClass()
{
}
```

O snippet de código **classi** também fornece a definição de uma classe chamada `MyClass`, mas o construtor e o destruidor padrão são definidos dentro da definição de classe:

```cpp
class MyClass
{
public:
    MyClass()
    {
    }

    ~MyClass()
    {
    }

private:

};
```

## <a name="for-vs-forr-vs-rfor"></a>para vs. forr vs rfor

Há três snippets **for** diferentes que fornecem diferentes tipos de loops `for`.

O trecho de código **rfor** fornece um loop for (link) [baseado em intervalo](/cpp/cpp/range-based-for-statement-cpp) . Este constructo é preferível em relação aos loops `for` baseados em índice.

```cpp
for (auto& i : v)
{

}
```

O trecho **for** fornece um `for` loop no qual a condição é baseada no comprimento (em `size_t` ) de um objeto.

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

O trecho de código **forr** fornece um loop reverso `for` no qual a condição é baseada no comprimento (em inteiros) de um objeto.

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

## <a name="the-destructor-snippet-"></a>O snippet de destruidor (~)

O trecho do destruidor ( **~** ) mostra um comportamento diferente em contextos diferentes. Se você inserir este snippet dentro de uma classe, ele fornecerá um destruidor para essa classe. Por exemplo, considerando o seguinte código:

```cpp
class SomeClass {

};
```

Se você inserir o snippet de destruidor, ele fornecerá um destruidor para `SomeClass`:

```cpp
class SomeClass {
    ~SomeClass()
    {

    }
};
```

Se você tentar inserir o snippet de destruidor fora de uma classe, ele fornecerá um destruidor com um nome de espaço reservado:

```cpp
~TypeNamePlaceholder()
{
```

## <a name="see-also"></a>Confira também

- [Snippets de código](../ide/code-snippets.md)