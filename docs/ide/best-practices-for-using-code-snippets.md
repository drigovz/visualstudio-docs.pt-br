---
title: Práticas recomendadas para usar snippets de código
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 08add20b59e3e14897d1870aa45fd6cce8698d96
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591704"
---
# <a name="best-practices-for-using-code-snippets"></a>Práticas recomendadas para usar snippets de código

O código em um snippet de código mostra somente a maneira mais simples de fazer algo. Para a maioria dos aplicativos, o código deve ser modificado para se adaptar ao aplicativo.

## <a name="handling-exceptions"></a>Tratamento de exceções

Normalmente, o snippet de código Try...Catch bloqueia a captura e gera todas as exceções novamente. Essa pode não ser a escolha certa para seu projeto. Para cada exceção, existem várias maneiras de responder. Para obter exemplos, confira [Como manipular uma exceção usando try/catch (C#)](/dotnet/csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch) e [Instrução Try...Catch...Finally (Visual Basic)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).

## <a name="file-locations"></a>Locais de arquivos

Quando você adaptar locais de arquivo ao seu aplicativo, deverá considerar o seguinte:

- Encontrando um local acessível. Os usuários podem não ter acesso à pasta *arquivos de programas* do computador, portanto, o armazenamento de arquivos com os arquivos de aplicativo pode não funcionar.

- Encontrando um local seguro. O armazenamento de arquivos na pasta raiz (*C \\ :*) não é seguro. Para dados de aplicativos, recomendamos a pasta *dados de aplicativos* . Para dados individuais do usuário, o aplicativo pode criar um arquivo para cada usuário na pasta *Documentos*.

- Usando um nome de arquivo válido. Você pode usar os controles <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> para reduzir a probabilidade de nomes de arquivo inválidos. Lembre-se de que entre o momento em que o usuário seleciona um arquivo e o momento em que o código manipula o arquivo, o arquivo poderá ser excluído. Além disso, o usuário poderá não ter permissões para gravar no arquivo.

## <a name="security"></a>Segurança

A segurança de um snippet depende do local em que ele é usado no código-fonte e de como ele é modificado quando estiver no código. A lista a seguir contém algumas das áreas que devem ser consideradas.

- Acesso ao arquivo e ao banco de dados

- Segurança de acesso do código

- Protegendo recursos (como logs de eventos, Registro)

- Armazenar segredos

- Verificando as entradas

- Passando dados para tecnologias de script

Para obter mais informações, consulte [Securing Applications](../ide/securing-applications.md).

## <a name="downloaded-code-snippets"></a>Snippets de código baixados

Os snippets de código do IntelliSense instalados pelo Visual Studio não são em si um risco de segurança. No entanto, eles podem criar riscos de segurança no aplicativo. Snippets baixados na Internet devem ser tratados como qualquer outro conteúdo baixado – com muito cuidado.

- Baixe snippets somente em sites confiáveis e use um software antivírus atualizado.

- Abra todos os arquivos de snippet baixados no Bloco de notas ou no editor de XML do Visual Studio e examine-os cuidadosamente antes de instalá-los. Procure os seguintes problemas:

  - O snippet de código poderá danificar o sistema se for executado. Leia atentamente o código-fonte antes de executá-lo.

  - O bloco URL de Ajuda do arquivo de snippet pode conter URLs que executam um arquivo de script mal-intencionado ou exibir um site ofensivo.

  - O snippet pode conter referências que são adicionadas silenciosamente ao projeto e podem ser carregadas em qualquer lugar do sistema. Essas referências podem ter sido baixadas no computador em que você baixou o snippet. Depois, o snippet de código pode fazer uma chamada a um método na referência que executa um código mal-intencionado. Para se proteger contra um ataque desse tipo, examine os blocos Importações e Referências do arquivo de snippet.

## <a name="see-also"></a>Confira também

- [Visual Basic trechos de código IntelliSense](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)
- [Protegendo aplicativos](../ide/securing-applications.md)
- [Snippets de código](../ide/code-snippets.md)
