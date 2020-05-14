---
title: Criando grupos reutilizáveis de botões | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddfba6701890f73ce6438ddc03a338912841a37d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739471"
---
# <a name="create-reusable-groups-of-buttons"></a>Criar grupos reutilizáveis de botões
Um grupo de comando é uma coleção de comandos que sempre aparecem juntos em um menu ou barra de ferramentas. Qualquer grupo de comando pode ser reutilizado atribuindo-o a diferentes menus-pai na seção CommandPlacements do arquivo *.vsct.*

 Os grupos de comando normalmente contêm botões, mas também podem conter outros menus ou caixas de combinação.

## <a name="to-create-a-reusable-group-of-buttons"></a>Para criar um grupo reutilizável de botões

1. Crie um projeto `ReusableButtons`VSIX chamado . Para obter mais informações, consulte [Criar uma extensão com um comando menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Quando o projeto for aberto, adicione um modelo de item de comando personalizado chamado **ReusableCommand**. No **Solution Explorer,** clique com o botão direito do mouse no nó do projeto e **selecione Adicionar** > **novo item**. Na **caixa de diálogo Adicionar novo item,** vá para A**Extensibilidade** **Visual C#** > e selecione **Comando Personalizado**. No **campo Nome,** na parte inferior da janela, altere o nome do arquivo de comando para *ReusableCommand.cs*.

3. No arquivo *.vsct,* vá até a seção Símbolos e encontre o elemento GuidSymbol que contém grupos e comandos para o projeto. Ele deve ser nomeado guidReusableCommandPackageCmdSet.

4. Adicione um IDSymbol para cada botão que você adicionará ao grupo, como no exemplo a seguir.

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     Por padrão, o modelo de item de comando cria um grupo chamado **MyMenuGroup** e um botão que tem o nome que você forneceu, juntamente com uma entrada IDSymbol para cada um.

5. Na seção Grupos, crie um elemento grupo que tenha os mesmos atributos GUID e ID que os dados na seção Símbolos. Você também pode usar um grupo existente ou usar a entrada fornecida pelo modelo de comando, como no exemplo a seguir. Este grupo aparece no menu **Ferramentas**

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>Para criar um grupo de botões para reutilização

1. Você pode colocar um comando ou menu em um grupo usando o grupo como pai na definição do comando ou menu, ou colocando o comando ou menu no grupo usando a seção '''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''

     Na seção Botões, defina um botão que tenha seu grupo como pai ou use o botão fornecido pelo modelo do pacote, conforme mostrado no exemplo a seguir.

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. Se um botão deve aparecer em mais de um grupo, crie uma entrada para ele na seção Comandos, que deve ser colocada após a seção Comandos. Defina os atributos GUID e ID do elemento CommandPlacement para corresponder aos do botão que deseja posicionar e, em seguida, defina o GUID e o ID de seu elemento Pai para os do grupo-alvo, conforme mostrado no exemplo a seguir.

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > O valor do campo Prioridade determina a posição do comando no novo grupo de comando. As prioridades definidas no elemento CommandPlacement sobrepõem as definidas na definição do item. Comandos com valores de prioridade mais baixos são exibidos antes de comandos com valores de prioridade mais elevados. Valores de prioridade duplicados são permitidos, mas a posição relativa dos comandos que têm o mesmo valor prioritário não pode ser garantida porque a ordem na qual o comando **devenv/setup** cria a interface final do registro pode não ser consistente.

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Para colocar um grupo reutilizável de botões em um menu

1. Crie uma entrada `CommandPlacements` na seção. Defina o GUID e `CommandPlacement` o ID do elemento para os do seu grupo e defina o GUID e o ID pai para os do local de destino.

    A seção Comandos Colocações deve ser colocada logo após a seção Comandos:

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    Um grupo de comando pode ser incluído em mais de um menu. O menu pai pode ser aquele que você [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] criou, um que é fornecido por (como descrito em *ShellCmdDef.vsct* ou *SharedCmdDef.vsct*), ou um que é definido em outro VSPackage. O número de camadas de paternidade é ilimitado [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] desde que o menu pai seja eventualmente conectado ou a um menu de atalho exibido por um VSPackage.

    O exemplo a seguir coloca o grupo na barra de ferramentas **do Solution Explorer,** à direita dos outros botões.

   ```xml
   <CommandPlacements>
       <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00">
         <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
       </CommandPlacement>
   </CommandPlacements>
   ```

   ```xml
   <CommandPlacements>
     <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup"
         priority="0x605">
       <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" />
     </CommandPlacement>
   </CommandPlacements>

   ```
