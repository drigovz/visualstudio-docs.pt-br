---
title: Elemento UsedCommand | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 91929038d77bcf14c6997f9b60551ed8c9c3b820
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58926360"
---
# <a name="usedcommand-element"></a>Elemento UsedCommand
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Permite que um VSPackage acessar um comando que é definido em outro arquivo. VSCT. Por exemplo, se o VSPackage usa o padrão **cópia** comando, que é definido pelo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] shell, você pode adicionar o comando a um menu ou barra de ferramentas sem ter que implementá-lo novamente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|GUID|Necessário. O GUID do par de ID de GUID que identifica o comando.|  
|id|Necessário. A ID do par de ID de GUID que identifica o comando.|  
|Condição|Opcional. Ver [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Nenhum||  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Agrupa elementos de UsedCommand e outros agrupamentos UsedCommands.|  
  
## <a name="remarks"></a>Comentários  
 Adicionando um comando para o `<UsedCommands>` informa a um VSPackage elemento, o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ambiente que o VSPackage exige que o comando. Você deve adicionar um `<UsedCommand>` elemento para qualquer comando que o pacote requer que não pode ser incluído em todas as versões e as configurações do Visual Studio. Por exemplo, se seu pacote chama um comando que é específico para o Visual C++, o comando não estará disponível para usuários do Visual Web Developer, a menos que você incluir um `<UsedCommand>` elemento para o comando.  
  
## <a name="example"></a>Exemplo  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Elemento UsedCommands](../extensibility/usedcommands-element.md)   
 [Arquivos da tabela de comandos do Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
