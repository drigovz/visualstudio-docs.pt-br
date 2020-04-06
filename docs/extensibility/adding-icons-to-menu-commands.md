---
title: Adicionando ícones aos comandos do menu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4b71f981472451766f526cf62e975e571cf46da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740158"
---
# <a name="add-icons-to-menu-commands"></a>Adicionar ícones aos comandos do menu
Os comandos podem aparecer em menus e barras de ferramentas. Nas barras de ferramentas, é comum que um comando seja exibido com apenas um ícone (para economizar espaço) enquanto nos menus um comando normalmente aparece com um ícone e um texto.

 Os ícones têm 16 pixels de largura por 16 pixels de altura e podem ser de 8 bits de profundidade de cor (256 cores) ou profundidade de cor de 32 bits (cor verdadeira). Ícones de cores de 32 bits são preferidos. Os ícones são tipicamente organizados em uma única linha horizontal em um único bitmap, embora vários bitmaps sejam permitidos. Este bitmap é declarado no arquivo *.vsct* juntamente com os ícones individuais disponíveis no bitmap. Consulte a referência para o [elemento Bitmaps](../extensibility/bitmaps-element.md) para obter mais detalhes.

## <a name="add-an-icon-to-a-command"></a>Adicione um ícone a um comando
 O procedimento a seguir pressupõe que você tenha um projeto VSPackage existente com um comando menu. Para saber como fazer isso, consulte [Criar uma extensão com um comando menu](../extensibility/creating-an-extension-with-a-menu-command.md).

1. Crie um bitmap com uma profundidade de cor de 32 bits. Um ícone é sempre 16 x 16, então este bitmap deve ter 16 pixels de altura e um múltiplo de 16 pixels de largura.

     Cada ícone é colocado no bitmap um ao lado do outro em uma única linha. Use o canal alfa para indicar locais de transparência em cada ícone.

     Se você usar uma profundidade de cor de `RGB(255,0,255)`8 bits, use magenta, como transparência. No entanto, os ícones de cores de 32 bits são preferidos.

2. Copie o arquivo de ícone sicompara o diretório *Recursos* em seu projeto VSPackage. No **Solution Explorer,** adicione o ícone ao projeto. (Selecione **Recursos**e, no menu de contexto, clique em **Adicionar,** em seguida, **Item existente**e selecione seu arquivo de ícone.)

3. Abra o arquivo *.vsct* no editor.

4. Adicione `GuidSymbol` um elemento com um nome de **testIcon**. Crie um GUID **(Ferramentas** > **Criar GUID,** selecione **Formato de Registro** e clique em **Copiar)** e cole-o no atributo. `value` O resultado deve ser assim:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. Adicione `<IDSymbol>` um para o ícone. O `name` atributo é o ID `value` do ícone, e indica sua posição na tira, se houver. Se houver apenas um ícone, adicione 1. O resultado deve ser assim:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. Crie `<Bitmap>` um `<Bitmaps>` na seção do arquivo *.vsct* para representar o bitmap que contém os ícones.

    - Defina `guid` o valor para `<GuidSymbol>` o nome do elemento que você criou na etapa anterior.

    - Defina `href` o valor para o caminho relativo do arquivo bitmap (neste **caso, recursos\\<nome\>do arquivo de ícone**.

    - Defina `usedList` o valor para o IDSymbol que você criou anteriormente. Este atributo especifica uma lista delimitada de vírgulas dos ícones a serem usados no VSPackage. Os ícones que não estão na lista são excluídos da compilação de formulários.

         O bloco Bitmap deve ficar assim:

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. No elemento `<Button>` existente, defina o `Icon` elemento para os valores GUIDSymbol e IDSymbol que você criou anteriormente. Aqui está um exemplo de um elemento Button com esses valores:

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. Teste seu ícone. Compile o projeto e comece a depuração. No caso experimental, encontre o comando. Ele deve mostrar o ícone que você adicionou.

## <a name="see-also"></a>Confira também
- [Estendendo menus e comandos](../extensibility/extending-menus-and-commands.md)
- [Referência de esquema VSCT XML](../extensibility/vsct-xml-schema-reference.md)
