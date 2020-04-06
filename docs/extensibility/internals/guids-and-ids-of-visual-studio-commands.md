---
title: GUIDs e IDs de Comandos do Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8932f23d301eabc97414bf76453d70336e0dabae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708247"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUIDs e IDs de comandos do Visual Studio
Os valores GUID e ID dos comandos incluídos no ambiente de desenvolvimento integrado (IDE) do Visual Studio são definidos em arquivos .vsct que são instalados como parte do Visual Studio SDK. Para obter mais informações, consulte [comandos, menus e grupos definidos pelo IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Para obter mais informações sobre como trabalhar com objetos IDE definidos em arquivos *.vsct,* consulte [Estender menus e comandos](../../extensibility/extending-menus-and-commands.md).

## <a name="find-a-command-definition"></a>Encontre uma definição de comando
 Como o Visual Studio define mais de 1000 comandos, é impraticável listá-los todos aqui. Em vez disso, siga estas etapas para localizar a definição de um comando.

### <a name="to-locate-a-command-definition"></a>Para localizar uma definição de comando

1. No Visual Studio, abra os seguintes arquivos no *<visual Studio SDK caminho\>de instalação \VisualStudioIntegration\Common\Inc\\ * pasta: *SharedCmdDef.vsct*, *ShellCmdDef.vsct*, *VsDbgCmdUsed.vsct*, *Venusmenu.vsct*.

    A maioria dos comandos do Visual Studio são definidos em *SharedCmdDef.vsct* e *ShellCmdDef.vsct*. *VsDbgCmdUsed.vsct* define comandos relativos ao depurador, e *Venusmenu.vsct* define comandos específicos para o desenvolvimento da Web.

2. Se o comando for um item do menu, observe o texto exato do item do menu. Se o comando for um botão em uma barra de ferramentas, observe o texto da dica de ferramenta que aparece quando você pausa nele.

3. Pressione **Ctrl**+**F** para abrir a caixa de diálogo **Encontrar.**

4. Na **caixa Encontre o que,** digite o texto que você anotou na etapa 2.

5. Verifique se **todos os documentos abertos** são exibidos na caixa Olhar **na** caixa.

6. Clique no botão **Encontrar a seguir** `<Strings>` até que o texto seja selecionado na seção de um [elemento Botão](../../extensibility/button-element.md).

    O `<Button>` elemento em que o comando aparece é a definição de comando.

   Quando você encontrar a definição de comando, você pode colocar uma cópia do comando em outro `guid` `id` menu ou barra de ferramentas criando um [elemento CommandPlacement](../../extensibility/commandplacement-element.md) que tenha o mesmo e valores que o comando. Para obter mais informações, consulte [Criar grupos reutilizáveis de botões](../../extensibility/creating-reusable-groups-of-buttons.md).

### <a name="special-cases"></a>Casos especiais
 Nos casos a seguir, o texto do menu ou do texto da dica de ferramenta pode não corresponder exatamente ao que está na definição do comando.

- Itens do menu que incluem um caractere sublinhado, como o comando **Imprimir** no menu **Arquivo,** no qual o *P* é sublinhado.

     Os caracteres precedidos pelo caractere ampersand (&) nos nomes dos itens do menu são exibidos como sublinhados. No entanto, os arquivos *.vsct* são escritos em XML, que usa o caractere ampersand (&) para indicar caracteres especiais e exige que um ampersand deve ser exibido como * &amp;amp;*. Portanto, em um arquivo *.vsct,* o comando **Imprimir** aparece como * &amp;amp; Imprimir*.

- Comandos que possuem texto **Save** \<dinâmico, como\>Save Current Filename, e itens de menu gerados dinamicamente, como os itens da lista **Arquivos recentes.**

     Não há uma maneira confiável de pesquisar em texto dinâmico. Em vez disso, encontre um grupo que hospede o comando desejado consultando [GUIDs e IDs de menus do Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) ou [GUIDs e IDs de barras de ferramentas do Visual Studio,](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)e pesquise no ID desse grupo. Se a definição de comando não tiver o grupo como [elemento Pai,](../../extensibility/parent-element.md) *pesquise SharedCmdPlace.vsct* e *ShellCmdPlace.vsct* (ou *VsDbgCmdPlace.vsct* para comandos de depurador) para um `<CommandPlacement>` elemento que define o pai do comando. *SharedCmdPlace.vsct*, *ShellCmdPlace.vsct*e *VsDbgCmdPlace.vsct* estão no * \<caminho\>de instalação do Visual\\ Studio SDK \VisualStudioIntegration\Common\Inc* pasta.

## <a name="see-also"></a>Confira também

- [Arquivos da tabela de comando do Visual Studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Referência de esquema VSCT XML](../../extensibility/vsct-xml-schema-reference.md)
