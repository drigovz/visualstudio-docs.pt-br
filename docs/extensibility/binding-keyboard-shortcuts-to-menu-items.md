---
title: Atalhos de teclado de vinculação aos itens do menu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94feafbc614be61aaa4eef9e26669c0fbe901ed5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740027"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>Vincular atalhos de teclado a itens de menu
Para vincular um atalho de teclado a um comando de menu personalizado, basta adicionar uma entrada ao arquivo *.vsct* do pacote. Este tópico explica como mapear um atalho de teclado para um botão personalizado, item do menu ou comando de barra de ferramentas e como aplicar o mapeamento do teclado no editor padrão ou limitá-lo a um editor personalizado.

 Para atribuir atalhos de teclado aos itens de menu do Visual Studio existentes, consulte [Identificar e personalizar atalhos de teclado](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="choose-a-key-combination"></a>Escolha uma combinação de chaves
 Muitos atalhos de teclado já são usados no Visual Studio. Você não deve atribuir o mesmo atalho a mais de um comando porque as ligações duplicadas são difíceis de detectar e também podem causar resultados imprevisíveis. Portanto, é uma boa ideia verificar a disponibilidade de um atalho antes de atribuí-lo.

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Para verificar a disponibilidade de um atalho de teclado

1. Na janela**Ambiente** **de opções de** >  **ferramentas,** > selecione **Teclado**.

2. Certifique-se de que **o novo atalho** in estiver definido como **Global**.

3. Na caixa **Pressionar teclas de atalho,** digite o atalho de teclado que deseja usar.

    Se o atalho já estiver usado no Visual Studio, o **atalho usado atualmente pela** caixa mostrará o comando que o atalho atualmente chama.

4. Experimente diferentes combinações de chaves até encontrar uma que não esteja mapeada.

   > [!NOTE]
   > Os atalhos de teclado que usam **Alt** podem abrir um menu e não executar diretamente um comando. Portanto, o **atalho atualmente usado pela** caixa pode estar em branco quando você digita um atalho que inclui **Alt**. Você pode verificar se o atalho não abre um menu fechando a caixa de diálogo **Opções** e pressionando as teclas.

   O procedimento a seguir pressupõe que você tenha um VSPackage existente com um comando menu. Se você precisar de ajuda para fazer isso, dê uma olhada em [Criar uma extensão com um comando menu](../extensibility/creating-an-extension-with-a-menu-command.md).

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Para atribuir um atalho de teclado a um comando

1. Abra o arquivo *.vsct* para o seu pacote.

2. Crie uma `<KeyBindings>` seção `<Commands>` vazia após o se ele ainda não estiver presente.

   > [!WARNING]
   > Para obter mais informações sobre as vinculações das tecla, consulte [Keybinding](../extensibility/keybinding-element.md).

    Na `<KeyBindings>` seção, `<KeyBinding>` crie uma entrada.

    Defina `guid` `id` os atributos e os do comando que você deseja invocar.

    Defina `mod1` o atributo como **Controle,** **Alt**ou **Shift**.

    A seção KeyBindings deve ser mais ou menos assim:

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   Se o atalho do teclado exigir `mod2` mais `key2` de duas teclas, defina os atributos.

   Na maioria das situações, **shift** não deve ser usado sem um segundo modificador porque pressioná-lo já faz com que a maioria das teclas alfanuméricas digite uma letra maiúscula ou um símbolo.

   Os códigos de chave virtual permitem que você acesse chaves especiais que não tenham um caractere associado a eles, por exemplo, teclas de função e a tecla **Backspace.** Para obter mais informações, consulte [códigos de chave virtual](/windows/desktop/inputdev/virtual-key-codes).

   Para disponibilizar o comando no editor do `editor` Visual `guidVSStd97`Studio, defina o atributo para .

   Para disponibilizar o comando apenas em um `editor` editor personalizado, defina o atributo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para o nome do editor personalizado gerado pelo Modelo de Pacote quando você criou o VSPackage que inclui o editor personalizado. Para encontrar o valor do `<Symbols>` nome, `<GuidSymbol>` procure `name` na seção`editorfactory`um nó cujo atributo termina em " ." Este é o nome do editor personalizado.

## <a name="example"></a>Exemplo
 Este exemplo liga o atalho do teclado **Ctrl**+**Alt**+ `MyPackage`**C** a um comando nomeado `cmdidMyCommand` em um pacote chamado .

```
<CommandTable>
. . .
<Commands>
. . .
</Commands>
<KeyBindings>
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />
</KeyBindings>
. . .
</CommandTable>
```

## <a name="example"></a>Exemplo
 Este exemplo liga o atalho do teclado **Ctrl**+**B** a um comando nomeado `cmdidBold` em um projeto chamado `TestEditor`. O comando está disponível apenas no editor personalizado e não em outros editores.

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>Confira também
- [Estendendo menus e comandos](../extensibility/extending-menus-and-commands.md)
