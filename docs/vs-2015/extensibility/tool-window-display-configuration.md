---
title: Configuração de exibição da janela de ferramentas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1af78bd58c42cf1312e36621011802e908c9e919
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186391"
---
# <a name="tool-window-display-configuration"></a>Configuração de exibição da janela de ferramentas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando um VSPackage registra uma janela de ferramentas, a posição padrão, o tamanho, o estilo de encaixe e outras informações de visibilidade são especificados em valores opcionais. Para obter mais informações sobre o registro da janela de ferramentas, consulte [janelas de ferramentas no registro](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>Informações de exibição da janela  
 A configuração básica de exibição de uma janela de ferramentas é armazenada em até seis valores opcionais:  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              (Default)       = reg_sz: <Package GUID>Name            = reg_sz: <name of tool window>Float           = reg_sz: <position>Style           = reg_sz: <dock style>Window          = reg_sz: <window GUID>Orientation     = reg_sz: <orientation>DontForceCreate = reg_dword: 0x00000000  
```  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|Name|REG_SZ|"Nome curto vai aqui"|Um nome curto que descreve a janela da ferramenta. Usado somente para referência no registro.|  
|Float|REG_SZ|"X1, Y1, X2, Y2"|Quatro valores separados por vírgula. X1, Y1 é a coordenada do canto superior esquerdo da janela de ferramentas. X2, Y2 é a coordenada do canto inferior direito. Todos os valores estão em coordenadas de tela.|  
|Estilo|REG_SZ|MDI<br /><br /> Barra<br /><br /> Vinculado<br /><br /> Com guias<br /><br /> "AlwaysFloat"|Uma palavra-chave que especifica o estado de exibição inicial da janela de ferramentas.<br /><br /> "MDI" = encaixado com janela MDI.<br /><br /> "Float" = flutuante.<br /><br /> "Vinculado" = vinculado a outra janela (especificada na entrada de janela).<br /><br /> "Com guias" = combinado com outra janela de ferramenta.<br /><br /> "AlwaysFloat" = não pode ser encaixado.<br /><br /> Para obter mais informações, consulte a seção comentários abaixo.|  
|Janela|REG_SZ|*\<GUID>*|O GUID de uma janela na qual a janela de ferramenta pode ser vinculada ou tabulada. O GUID pode pertencer a um de seus próprios Windows ou a uma das janelas no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE.|  
|Orientação|REG_SZ|Mantida<br /><br /> Adequada<br /><br /> Melhor<br /><br /> Resultado|Consulte a seção de comentários abaixo.|  
|DontForceCreate|REG_DWORD|0 ou 1|Quando essa entrada está presente e seu valor não é zero, a janela é carregada, mas não é exibida imediatamente.|  
  
### <a name="comments"></a>Comentários  
 A entrada de orientação define a posição onde a janela de ferramentas se encaixa quando sua barra de título é clicada duas vezes. A posição é relativa à janela especificada na entrada da janela. Se a entrada de estilo for definida como "vinculada", a entrada de orientação poderá ser "esquerda", "direita", "superior" ou "inferior". Se a entrada de estilo for "com guias", a entrada de orientação poderá ser "esquerda" ou "direita" e especifica o local em que a guia é adicionada. Se a entrada de estilo for "Float", a janela de ferramentas flutuará primeiro. Quando a barra de título é clicada duas vezes, a orientação e as entradas de janela se aplicam e a janela usa o estilo "com guias". Se a entrada de estilo for "AlwaysFloat", a janela de ferramentas não poderá ser encaixada. Se a entrada de estilo for "MDI", a janela de ferramentas será vinculada à área MDI e a entrada da janela será ignorada.  
  
### <a name="example"></a>Exemplo  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {A0C5197D-0AC7-4B63-97CD-8872A789D233}\  
              (Default)       = reg_sz: {DA9FB551-C724-11D0-AE1F-00A0C90FFFC3}  
              DontForceCreate = reg_dword: 0x00000000  
              Float           = reg_sz: 100,100,450,300  
              Name            = reg_sz: Bookmarks  
              Orientation     = reg_sz: Left  
              Style           = reg_sz: Tabbed  
              Window          = reg_sz: {34E76E81-EE4A-11D0-00A0C90FFFC3}  
```  
  
## <a name="tool-window-visibility"></a>Visibilidade da janela de ferramentas  
 Os valores na subchave de visibilidade opcional determinam as configurações de visibilidade da janela de ferramentas. Os nomes dos valores são usados para armazenar os GUIDs de comandos que exigem a visibilidade da janela. Se o comando for executado, o IDE garante que a janela de ferramentas seja criada e tornada visível.  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              Visibility\  
                (Default) = reg_sz:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_sz:  
```  
  
|Nome|Tipo|Dados|Descrição|  
|----------|----------|----------|-----------------|  
|(Padrão)|REG_SZ|Nenhum|Deixe em branco.|  
|*\<GUID>*|REG_DWORD ou REG_SZ|0 ou uma cadeia de caracteres descritiva.|Opcional. O nome da entrada deve ser o GUID de um comando que requer visibilidade. O valor apenas contém uma cadeia de caracteres informativa. Normalmente, o valor é um `reg_dword` definido como 0.|  
  
### <a name="example"></a>Exemplo  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {EEFA5220-E298-11D0-8F78-00A0C9110057}\  
              Visibility\  
                (Default) = reg_sz:  
                {93694fa0-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
                {9DA22B82-6211-11d2-9561-00600818403B} = reg_dword: 0x00000000  
                {adfc4e66-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Conceitos básicos do VSPackage](../misc/vspackage-essentials.md)
