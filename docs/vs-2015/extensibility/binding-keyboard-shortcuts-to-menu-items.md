---
title: Vinculando atalhos de teclado a itens de menu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e362a61c5ecab78c332eb5e077a02ee4e9e3fa9b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295622"
---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>Associando atalhos de teclado a itens de menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para associar um atalho de teclado a um comando de menu personalizado, basta adicionar uma entrada ao arquivo. vsct do pacote. Este tópico explica como mapear um atalho de teclado para um botão personalizado, um item de menu ou um comando de barra de ferramentas e como aplicar o mapeamento de teclado no editor padrão ou limitá-lo a um editor personalizado.  
  
 Para atribuir atalhos de teclado a itens de menu existentes do Visual Studio, consulte [identificando e personalizando atalhos de teclado](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="choosing-a-key-combination"></a>Escolhendo uma combinação de teclas  
 Muitos atalhos de teclado já são usados no Visual Studio. Você não deve atribuir o mesmo atalho a mais de um comando porque associações duplicadas são difíceis de detectar e também podem causar resultados imprevisíveis. Portanto, é uma boa ideia verificar a disponibilidade de um atalho antes de atribuí-lo.  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Para verificar a disponibilidade de um atalho de teclado  
  
1. Na janela **ferramentas/opções/ambiente** , selecione **teclado**.  
  
2. Certifique-se de que **usar o novo atalho no** esteja definido como **global**.  
  
3. Na caixa **pressione teclas de atalho** , digite o atalho de teclado que você deseja usar.  
  
    Se o atalho já estiver sendo usado no Visual Studio, o **atalho usado no momento pelo** Box mostrará o comando que o atalho chama atualmente.  
  
4. Tente combinações diferentes de chaves até encontrar uma que não esteja mapeada.  
  
   > [!NOTE]
   > Os atalhos de teclado que usam ALT podem abrir um menu e não executar diretamente um comando. Portanto, o **atalho usado atualmente pelo** box pode estar em branco quando você digita um atalho que inclui alt. Você pode verificar se o atalho não abre um menu fechando a caixa de diálogo **Opções** e, em seguida, pressionando as teclas.  
  
   O procedimento a seguir pressupõe que você tenha um VSPackage existente com um comando de menu. Se precisar de ajuda para fazer isso, dê uma olhada na [criação de uma extensão com um comando de menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Para atribuir um atalho de teclado a um comando  
  
1. Abra o arquivo. vsct para seu pacote.  
  
2. Crie uma seção `<KeyBindings>` vazia após a `<Commands>` se ela ainda não estiver presente.  
  
   > [!WARNING]
   > Para obter mais informações sobre associações de chave, consulte [KeyBinding](../extensibility/keybinding-element.md).  
  
    Na seção `<KeyBindings>`, crie uma entrada de `<KeyBinding>`.  
  
    Defina os atributos `guid` e `id` para aqueles do comando que você deseja invocar.  
  
    Defina o atributo `mod1` como **Control**, **ALT**ou **Shift**.  
  
    A seção keybindings deve ser semelhante a esta:  
  
   ```xml  
   <KeyBindings>  
       <KeyBinding guid="<name of command set>" id="<name of command id>"  
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
   </KeyBindings>  
  
   ```  
  
   Se o atalho de teclado exigir mais de duas chaves, defina os atributos `mod2` e `key2`.  
  
   Na maioria das situações, **Shift** não deve ser usada sem um segundo modificador, pois pressioná-la já faz com que a maioria das chaves alfanuméricas digite uma letra maiúscula ou um símbolo.  
  
   Os códigos de chave virtual permitem que você acesse chaves especiais que não têm um caractere associado a elas, por exemplo, chaves de função e a tecla **Backspace** . Para obter mais informações, consulte [códigos-chave virtuais](https://go.microsoft.com/fwlink/?LinkID=105932).  
  
   Para disponibilizar o comando no editor do Visual Studio, defina o atributo `editor` como `guidVSStd97`.  
  
   Para disponibilizar o comando somente em um editor personalizado, defina o atributo `editor` como o nome do editor personalizado que foi gerado pelo modelo de pacote de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] quando você criou o VSPackage que inclui o editor personalizado. Para localizar o valor do nome, procure na seção `<Symbols>` por um nó `<GuidSymbol>` cujo atributo `name` termina em "`editorfactory`". Este é o nome do editor personalizado.  
  
## <a name="example"></a>Exemplo  
 Este exemplo associa o atalho de teclado CTRL + ALT + C a um comando chamado `cmdidMyCommand` em um pacote chamado `MyPackage`.  
  
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
 Este exemplo associa o atalho de teclado CTL + B a um comando chamado `cmdidBold` em um projeto chamado `TestEditor`. O comando está disponível somente no editor personalizado e não em outros editores.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>Consulte também  
 [Ampliar menus e comandos](../extensibility/extending-menus-and-commands.md)
