---
title: Práticas recomendadas para usar snippets de código
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d95b1b95d1859d29f82f7de45aa6ddb9cde7554f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53908912"
---
# <a name="best-practices-for-using-code-snippets"></a>Práticas recomendadas para usar snippets de código

O código em um snippet de código mostra somente a maneira mais simples de fazer algo. Para a maioria dos aplicativos, o código deve ser modificado para se adaptar ao aplicativo.

## <a name="handling-exceptions"></a>Tratando exceções

Normalmente, o snippet de código Try...Catch bloqueia a captura e gera todas as exceções novamente. Essa pode não ser a escolha certa para seu projeto. Para cada exceção, existem várias maneiras de responder. Para ver mais exemplos, veja [Como: Tratar uma exceção usando try/catch (C#)](/dotnet/csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch) e [Instrução Try...Catch...Finally (Visual Basic)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).

## <a name="file-locations"></a>Locais de arquivo

Quando você adaptar locais de arquivo ao seu aplicativo, deverá considerar o seguinte:

- Encontrando um local acessível. Os usuários poderão não ter acesso à pasta *Arquivos de Programas do computador*; portanto, armazenar arquivos com os arquivos do aplicativo pode não funcionar.

- Encontrando um local seguro. Não é seguro armazenar arquivos na pasta raiz (*C:\\*). Para dados de aplicativo, recomendamos a pasta *Dados de Aplicativos*. Para dados individuais do usuário, o aplicativo pode criar um arquivo para cada usuário na pasta *Documentos*.

- Usando um nome de arquivo válido. Você pode usar os controles <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> para reduzir a probabilidade de nomes de arquivo inválidos. Lembre-se de que entre o momento em que o usuário seleciona um arquivo e o momento em que o código manipula o arquivo, o arquivo poderá ser excluído. Além disso, o usuário poderá não ter permissões para gravar no arquivo.

## <a name="security"></a>Segurança

A segurança de um snippet depende do local em que ele é usado no código-fonte e de como ele é modificado quando estiver no código. A lista a seguir contém algumas das áreas que devem ser consideradas.

- Acesso ao arquivo e ao banco de dados

- Segurança de acesso do código

- Protegendo recursos (como logs de eventos, Registro)

- Armazenando segredos

- Verificando as entradas

- Passando dados para tecnologias de script

Para saber mais, veja [Como proteger aplicativos](../ide/securing-applications.md).

## <a name="downloaded-code-snippets"></a>Snippets de código baixados

Os snippets de código do IntelliSense instalados pelo Visual Studio não são em si um risco de segurança. No entanto, eles podem criar riscos de segurança no aplicativo. Snippets baixados na Internet devem ser tratados como qualquer outro conteúdo baixado – com muito cuidado.

- Baixe snippets somente em sites confiáveis e use um software antivírus atualizado.

- Abra todos os arquivos de snippet baixados no Bloco de notas ou no editor de XML do Visual Studio e examine-os cuidadosamente antes de instalá-los. Procure os seguintes problemas:

    - O snippet de código poderá danificar o sistema se for executado. Leia atentamente o código-fonte antes de executá-lo.

    - O bloco URL de Ajuda do arquivo de snippet pode conter URLs que executam um arquivo de script mal-intencionado ou exibir um site ofensivo.

    - O snippet pode conter referências que são adicionadas silenciosamente ao projeto e podem ser carregadas em qualquer lugar do sistema. Essas referências podem ter sido baixadas no computador em que você baixou o snippet. Depois, o snippet de código pode fazer uma chamada a um método na referência que executa um código mal-intencionado. Para se proteger contra um ataque desse tipo, examine os blocos Importações e Referências do arquivo de snippet.

## <a name="see-also"></a>Consulte também

- [Snippets de código do Visual Basic IntelliSense](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)
- [Como proteger aplicativos](../ide/securing-applications.md)
- [Snippets de código](../ide/code-snippets.md)