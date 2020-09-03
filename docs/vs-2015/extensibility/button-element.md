---
title: Elemento Button | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 58f63968ed02f49b0ccfa4dda24f684fed339bc4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184547"
---
# <a name="button-element"></a>Elemento Button
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Define um elemento com o qual o usuário pode interagir. Os botões podem ser de tipos diferentes: Button, MenuButton e SplitDropDown.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">  
  <Parent>... </Parent>  
  <Icon>... </Icon>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Button>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|guid|Obrigatórios. GUID do identificador de comando GUID/ID.|  
|id|Obrigatórios. ID do identificador de comando de GUID/ID.|  
|priority|Opcional. Um valor numérico que especifica a prioridade.|  
|tipo|Opcional. Um valor enumerado que especifica o tipo de botão.<br /><br /> Se não for fornecido, o usará o botão.<br /><br /> Botão<br /> Um comando padrão que aparece nas barras de ferramentas (normalmente, como um botão de icônico), menus e menus de contexto.<br /><br /> MenuButton<br /> Um item de menu que não executa um comando, mas produz outro menu.<br /><br /> SplitDropDown<br /> Controles, como os botões desfazer e refazer na barra de ferramentas padrão do Microsoft Word.|  
|Condição|Opcional. Consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento pai](../extensibility/parent-element.md)|Opcional. O elemento pai do botão.|  
|[Elemento Icon](../extensibility/icon-element.md)|Opcional. O ícone associado ao botão.|  
|[Elemento Command Flag](../extensibility/command-flag-element.md)|Obrigatórios. Os valores de CommandFlag válidos para um botão são os seguintes.<br /><br /> - AllowParams<br /><br /> - CommandWellOnly<br /><br /> -Defaultdesabilitoud<br /><br /> -Invisible<br /><br /> - DontCache<br /><br /> - DynamicItemStart<br /><br /> - DynamicVisibility<br /><br /> - FixMenuController<br /><br /> - IconAndText<br /><br /> - NoButtonCustomize<br /><br /> -Nopersonalizar<br /><br /> - NoKeyCustomize<br /><br /> - NoShowOnMenuController<br /><br /> -PICT<br /><br /> -Exec<br /><br /> - ProfferedCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> -Textchanges<br /><br /> - TextChangesButton<br /><br /> - TextContextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> - TextMenuUseButton<br /><br /> -Somente|  
|[Elemento Strings](../extensibility/strings-element.md)|Obrigatórios. O [elemento ButtonText](../extensibility/buttontext-element.md) filho deve ser definido.|  
|Anotação|Comentário opcional.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento Buttons](../extensibility/buttons-element.md)|Elementos de botão de grupos.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define um botão em um arquivo. vsct.  
   
 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```

## <a name="see-also"></a>Consulte Também  
 [Arquivos .Vsct (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
