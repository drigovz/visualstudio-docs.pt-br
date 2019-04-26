---
title: Suporte para aplicativos em árabe e hebraico
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Hebrew character display, creating applications
- bidirectional language support, about bidirectional language support
- Arabic language, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d09ad8644c30be76c38cf4b819d09ee1c470cb39
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62793433"
---
# <a name="create-applications-in-bidirectional-languages"></a>Criar aplicativos em idiomas bidirecionais

É possível usar o Visual Studio para criar aplicativos que exibem o texto corretamente em idiomas escritos da direita para a esquerda, incluindo árabe e hebraico. Para alguns recursos, é possível apenas definir as propriedades. Em outros casos, é necessário implementar recursos no código.

> [!NOTE]
> Para inserir e exibir idiomas bidirecionais, você precisa trabalhar com uma versão do Windows que está configurada com o idioma apropriado. Essa pode ser uma versão em inglês do Windows com o pacote de idioma apropriado instalado, ou a versão localizada do Windows.

## <a name="types-of-applications-that-support-bidirectional-languages"></a>Tipos de aplicativos que dão suporte a idiomas bidirecionais

- Aplicativos do Windows

   É possível criar aplicativos totalmente bidirecionais que incluem suporte para texto bidirecional, sentido de leitura da direita para a esquerda e espelhamento (reversão do layout de janelas, menus, caixas de diálogo e assim por diante). Com exceção do espelhamento, esses recursos estão disponíveis por padrão ou como configurações de propriedades. Há suporte inerente para o espelhamento em alguns recursos, como caixas de mensagem. No entanto, em outros casos, é necessário implementar o espelhamento no código. Para obter mais informações, confira [Suporte bidirecional para aplicativos do Windows Forms](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications).

- Aplicativos Web

   Os serviços Web dão suporte ao recebimento e ao envio de textos UTF-8 e Unicode, tornando-os adequados para aplicativos que envolvem idiomas bidirecionais. Os aplicativos cliente Web dependem de navegadores para sua interface do usuário e, portanto, o grau de suporte bidirecional em um aplicativo Web depende do nível de suporte do navegador do usuário a essas funcionalidades bidirecionais. No Visual Studio, é possível criar aplicativos com suporte para texto em árabe ou hebraico, sentido de leitura da direita para a esquerda, codificação de arquivos e configurações da cultura local. Para saber mais, confira [Suporte bidirecional para aplicativos Web ASP.NET](https://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03).

Os aplicativos de console não incluem o suporte de texto para idiomas bidirecionais. Esta é uma consequência de como o Windows funciona com aplicativos de console.

## <a name="fully-supported-features"></a>Recursos totalmente compatíveis

Em tempo de design no Visual Studio, é possível usar idiomas bidirecionais das seguintes maneiras:

- **Entrada de texto**

   O Visual Studio dá suporte ao Unicode; portanto, se o sistema estiver definido com a localidade e o idioma de entrada apropriados, será possível inserir texto em árabe ou hebraico. (O suporte para árabe inclui Kashida e Sinais Diacríticos.)

- **Nomes de objetos**

   Use idiomas bidirecionais para atribuir nomes a soluções, projetos, arquivos, pastas e assim por diante. No código, use idiomas bidirecionais para os nomes de variáveis, classes, objetos, atributos, metadados e outros elementos.

- **Codificação de arquivos**

   É possível salvar e abrir arquivos com uma codificação Unicode ou específica a um idioma. Para obter mais informações, confira [Como: Salvar e abrir arquivos com codificação](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="features-with-limited-support"></a>Recursos com suporte limitado

### <a name="right-to-left-reading-order"></a>Sentido de leitura da direita para a esquerda

Por padrão, os controles de entrada de texto no Visual Studio usam o sentido de leitura da esquerda para a direita. Na maioria dos casos, é possível usar gestos do Windows padrão para mudar o sentido de leitura. Por exemplo, é possível pressionar **Ctrl**+**Shift Direita** para mudar para a janela **Propriedades** para dar suporte ao sentido de leitura da direita para a esquerda em valores da propriedade. No entanto, o sentido de leitura da direita para a esquerda não é compatível em todos os lugares do Visual Studio:

- Caixas de seleção, listas suspensas e outros controles em caixas de diálogo do Visual Studio sempre usam o sentido de leitura da esquerda para a direita.

- O editor de código (e o editor de texto) não dão suporte ao sentido de leitura da direita para a esquerda. Insira o texto em um idioma bidirecional, mas com o sentido de leitura sempre sendo da esquerda para a direita.

## <a name="arabic-or-hebrew-object-names"></a>Nomes de objeto em árabe ou hebraico

É possível usar um texto em árabe ou hebraico para atribuir nomes a pastas, variáveis ou outros objetos. Ao trabalhar com o árabe, é possível usar qualquer caractere árabe, incluindo Kashida e Sinais Diacríticos.

Os seguintes elementos podem ser nomeados usando o árabe ou o hebraico e são manipulados corretamente no Visual Studio:

- Nomes de solução, projeto e arquivo, incluindo as pastas incluídas no caminho do projeto. O **Gerenciador de Soluções** exibe os nomes de elemento e de solução corretamente.

- Conteúdo do arquivo. É possível abrir ou salvar arquivos com a codificação Unicode ou com uma página de código selecionada.

    > [!NOTE]
    > O editor de código não dá suporte ao sentido de leitura da direita para a esquerda.

- Elementos de dados. O **Gerenciador de Servidores** exibe esses elementos corretamente e permite que sejam editados.

- Elementos copiados para a Área de Transferência do Windows.

- Atributos e metadados.

- Valores da propriedade. É possível usar um texto em árabe ou hebraico na janela **Propriedades**. A janela permite mudar entre o sentido de leitura da direita para a esquerda e da esquerda para a direita usando pressionamentos de tecla padrão do Windows (**Ctrl**+**Shift Direita** para direita para a esquerda e **Ctrl**+**Shift Esquerda** para esquerda para a direita).

- Código e texto literal. No editor de código, é possível usar o árabe ou o hebraico para nomear classes, funções, variáveis, propriedades, literais de cadeia de caracteres, atributos e assim por diante. No entanto, o editor não dá suporte ao sentido de leitura da direita para a esquerda; o texto sempre começa na margem esquerda.

    > [!TIP]
    > Você deve colocar literais de cadeia de caracteres em arquivos de recurso, em vez de fazer hard-coding nos programas. Para saber mais, veja [Recursos em aplicativos da área de trabalho (.NET Framework)](/dotnet/framework/resources/index).

    > [!NOTE]
    > Você deve ser consistente na forma como se refere aos objetos nomeados em árabe e hebraico. Por exemplo, se você usar Kashida ao nomear uma variável em árabe, deverá sempre usar Kashida ao se referir a essa variável; caso contrário, ocorrerão erros.

- Comentários sobre o código. É possível criar comentários em árabe ou hebraico. Você também pode usar esses idiomas na ferramenta de construtor de comentários.