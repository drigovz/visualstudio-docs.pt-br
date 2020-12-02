---
title: Suporte para árabe e hebraico
description: Saiba como exibir texto em árabe e Hebraico e inserir texto bidirecional para nomes de objeto e valores.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Hebrew character display [Visual Studio]
- bidirectional language support
- Arabic, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa2520527259c476f84d83cdff81d9f96bc2bbd7
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96478959"
---
# <a name="support-for-bidirectional-languages-in-visual-studio"></a>Suporte para idiomas bidirecionais no Visual Studio

O Visual Studio pode exibir um texto em árabe e hebraico corretamente e permite que você insira o texto bidirecional para valores e nomes de objeto.

> [!NOTE]
> Para inserir e exibir idiomas bidirecionais, você precisa trabalhar com uma versão do Windows que está configurada com o idioma apropriado. Essa pode ser uma versão em inglês do Windows com o pacote de idioma apropriado instalado, ou a versão localizada do Windows.

## <a name="fully-supported-features"></a>Recursos totalmente compatíveis

Em tempo de design no Visual Studio, você pode usar idiomas bidirecionais ao inserir texto, nomear objetos e salvar e abrir arquivos.

### <a name="text-entry"></a>Entrada de texto

O Visual Studio dá suporte ao Unicode; portanto, se o sistema estiver definido com a localidade e o idioma de entrada apropriados, será possível inserir texto em árabe ou hebraico. (O suporte para árabe inclui Kashida e Sinais Diacríticos.)

### <a name="arabic-or-hebrew-object-names"></a>Nomes de objeto em árabe ou hebraico

Use idiomas bidirecionais para atribuir nomes a soluções, projetos, arquivos, pastas e assim por diante. No código, use idiomas bidirecionais para os nomes de variáveis, classes, objetos, atributos, metadados e outros elementos. Ao trabalhar com o árabe, é possível usar qualquer caractere árabe, incluindo Kashida e Sinais Diacríticos.

Os seguintes elementos podem ser nomeados usando o árabe ou o hebraico e são manipulados corretamente pelo Visual Studio:

- Nomes de solução, projeto e arquivo, incluindo as pastas incluídas no caminho do projeto.

   O **Gerenciador de Soluções** exibe os nomes de elemento e de solução corretamente.

- Conteúdo do arquivo.

   É possível abrir ou salvar arquivos com a codificação Unicode ou com uma página de código selecionada.

- Elementos de dados.

   O **Gerenciador de Servidores** exibe esses elementos corretamente e você pode editá-los.

- Elementos copiados para a Área de Transferência do Windows.

- Atributos e metadados.

- Valores de propriedade.

   Você pode usar o texto em árabe ou Hebraico na janela **Propriedades** . A janela permite que você alterne entre a ordem de leitura da direita para a esquerda e da esquerda para a direita usando pressionamentos de tecla padrão do Windows (**Ctrl** + **RightShift** para a direita para a esquerda e **Ctrl** + **LeftShift** da esquerda para a direita).

- Código e texto literal.

   No editor de código, é possível usar o árabe ou o hebraico para nomear classes, funções, variáveis, propriedades, literais de cadeia de caracteres, atributos e assim por diante. No entanto, o editor não dá suporte ao sentido de leitura da direita para a esquerda; o texto sempre começa na margem esquerda.

   > [!TIP]
   > Você deve colocar literais de cadeia de caracteres em arquivos de recurso, em vez de fazer hard-coding nos programas. Para saber mais, veja [Recursos em aplicativos da área de trabalho (.NET Framework)](/dotnet/framework/resources/index).

   > [!NOTE]
   > Você deve ser consistente na forma como se refere aos objetos nomeados em árabe e hebraico. Por exemplo, se você usar Kashida ao nomear uma variável em árabe, deverá sempre usar Kashida ao se referir a essa variável; caso contrário, ocorrerão erros.

- Comentários sobre o código. É possível criar comentários em árabe ou hebraico. Você também pode usar esses idiomas na ferramenta de construtor de comentários.

### <a name="file-encoding"></a>Codificação de arquivo

É possível salvar e abrir arquivos com uma codificação Unicode ou específica a um idioma. Para obter mais informações, consulte [como salvar e abrir arquivos com codificação](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="right-to-left-reading-order"></a>Sentido de leitura da direita para a esquerda

O Visual Studio tem suporte limitado para o sentido de leitura da direita para a esquerda. Por padrão, os controles de entrada de texto no Visual Studio usam o sentido de leitura da esquerda para a direita. Na maioria dos casos, é possível usar gestos do Windows padrão para mudar o sentido de leitura. Por exemplo, você pode pressionar **Ctrl** + **RightShift** para alternar a janela **Propriedades** para oferecer suporte à ordem de leitura da direita para a esquerda para valores de propriedade.

Não há suporte para o sentido de leitura da direita para a esquerda nos seguintes locais do Visual Studio:

- Caixas de seleção, listas suspensas e outros controles em caixas de diálogo do Visual Studio sempre usam o sentido de leitura da esquerda para a direita.

- O editor de código (e o editor de texto) não dão suporte ao sentido de leitura da direita para a esquerda. Insira o texto em um idioma bidirecional, mas com o sentido de leitura sempre sendo da esquerda para a direita.

## <a name="see-also"></a>Confira também

- [Desenvolver aplicativos localizados e globalizados](globalizing-and-localizing-applications.md)
