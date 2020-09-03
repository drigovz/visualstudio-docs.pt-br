---
title: Sobre a janela de registros | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, about Registers window
- debugging [Visual Studio], Registers window
ms.assetid: ab354047-053e-4f94-8ac1-26e761442b6f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4deaf03013b6e28ea02e6ec7412bd23a05f1b87e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72738257"
---
# <a name="about-the-registers-window-in-visual-studio-c-c-visual-basic-f"></a>Sobre a janela de registros no Visual Studio (C#, C++, Visual Basic, F #)

A janela **Registros** só ficará disponível se a depuração do nível de endereços estiver habilitada na caixa de diálogo **Opções**, nó **Depuração**.

 Os registros são locais especiais dentro de um processador (CPU) que são usados para armazenar partes pequenas de dados em que o processador está trabalhando ativamente. Compilar ou interpretar o código-fonte gera instruções que movem dados da memória para os registros e de volta, conforme o necessário. Acessar dados em registros é muito rápido comparado a acessar dados na memória. Sendo assim, o código que permite que o processador mantenha dados em um registro e os acesse repetidamente tende a ser executado mais rápido do que o código que requer que o processador carregue e descarregue registros constantemente. Para que o compilador possa manter os dados nos registros e executar outras otimizações, evite usar variáveis globais e confie em variáveis locais o máximo possível. O código escrito dessa maneira tem boa a localidade de referência. Em algumas linguagens, por exemplo, C/C++, o desenvolvedor pode declarar uma variável do registro, que diz ao compilador para tentar o melhor possível para manter a variável em um registro constantemente. Para saber mais, veja [Registrar palavra-chave](https://msdn.microsoft.com/library/5b66905a-2f7f-4918-bb55-5e66d4bc50f9).

 Os registros podem ser divididos em dois tipos: uso geral e finalidade especial. Os registros de uso geral mantêm dados para operações gerais, por exemplo, adicionar dois números ou referenciar um elemento em uma matriz. Os registros de finalidade especial têm finalidades específicas e significado especializado. Um bom exemplo é o registro do ponteiro de pilha, que o processador usa para manter controle da pilha de chamadas do programa. Como programador, você provavelmente não manipulará o ponteiro de pilhas diretamente. No entanto, é essencial para o funcionamento correto do programa porque, sem o ponteiro de pilha, o processador não saberia para onde retornar ao término de uma chamada de função.

 A maioria de registros de uso geral contém apenas um elemento de dados. Por exemplo, um único inteiro, número de ponto flutuante ou elemento de uma matriz. Alguns processadores mais novos têm registros maiores, chamados de registros de vetor, que podem manter uma matriz de dados pequena. Como eles contêm tantos dados, os registros de vetor permitem que as operações que envolvem as matrizes sejam executadas muito rapidamente. Os registros de vetor foram usados primeiro em supercomputadores caros de alto desempenho, mas agora estão se tornando disponíveis em microprocessadores onde estão acostumados a grande vantagem em operações gráficas intensivas.

 Um processador normalmente tem dois conjuntos de registros de uso geral, um otimizado para operações de ponto flutuante e o outro para operações de inteiros. Não é surpresa eles serem chamados de registros de pontos flutuante e inteiros.

 O código gerenciado é compilado em tempo de execução para o código nativo que acessa os registros físicos do microprocessador. A janela **Registros** exibe físicos esses registros físicos para Common Language Runtime ou o código nativo. A janela **Registros** não exibe informações de registro do script ou do aplicativo SQL, porque o script e o SQL são linguagens que não dão suporte ao conceito de registros.

 Para saber mais sobre como exibir a janela **Registros**, confira [Como usar a janela Registros](../debugger/how-to-use-the-registers-window.md).

 Quando você examinar a janela de **registros** , verá entradas como `EAX = 003110D8` .

 O símbolo à esquerda do `=` sinal é o nome do registro, `EAX` , nesse caso. O número à direita do sinal `=` representa o conteúdo do registro.

 A janela **Registros** permite fazer mais do que apenas exibir o conteúdo de um registro. Quando você está no modo de interrupção em código nativo, pode clicar no conteúdo de um registro e editar o valor. Isso não é algo que você deve fazer aleatoriamente. A menos que você compreenda o registro que está editando, e os dados que ele contém, o resultado de uma edição descuidada provavelmente será uma falha de programa ou alguma outra consequência indesejada. Infelizmente, uma explicação detalhada dos conjuntos de registro dos vários processadores Intel e compatíveis com Intel vai além do escopo dessa breve introdução.

## <a name="register-groups"></a>Registrar grupos

Para reduzir a confusão, a janela **Registros** organiza os registros em grupos. Se você clicar com o botão direito na janela **Registros**, verá um menu de atalho contendo uma lista de grupos que você pode exibir ou ocultar como achar melhor.

## <a name="register-flags"></a>Registrar sinalizadores

Para processadores Intel x86, você pode ver os seguintes sinalizadores na janela de **registros** . Durante uma sessão de depuração, você também pode editar esses sinalizadores.

|Sinalizador|Definir valor|
|-|-|
|Estouro|OV = 1|
|Direção|PARA CIMA = 1|
|Atividades|EI = 1|
|Assinar|PL = 1|
|Zero|ZR = 1|
|Transporte auxiliar|AC = 1|
|Parity|PE = 1|
|Carry|CY = 1|

## <a name="see-also"></a>Confira também
- [Como usar a janela Registros](../debugger/how-to-use-the-registers-window.md)
- [Introdução ao depurador](../debugger/debugger-feature-tour.md)