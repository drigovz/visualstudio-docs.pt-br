---
title: Elemento extern | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 17477b7eb60aa332f6910019e28f4c53aa31ebf1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58927717"
---
# <a name="extern-element"></a>Elemento Extern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O elemento Extern faz referência a todos os arquivos externos de cabeçalho (. h) para mesclar com o arquivo. VSCT em tempo de compilação. Os arquivos a serem mescladas devem estar no caminho de inclusão fornecido ao compilador VSCT ou referenciado por um [incluem o elemento](../extensibility/include-element.md). Os arquivos podem ser outros arquivos. VSCT ou arquivos de cabeçalho C++.  
  
 As definições em arquivos de cabeçalho devem estar no formato "#define [Symbol] [valor]" o valor pode ser outro símbolo, caso ele seja definido anteriormente. Definições podem ser usadas em instruções condicionais de itens de comando. Qualquer símbolo, na verdade não usado será descartado.  
  
 Elemento CommandTable  
Elemento Extern  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|{1&gt;href&lt;1}|Necessário. O caminho para o arquivo de cabeçalho:<br /><br /> href="stdidcmd.h"|  
|Condição|Opcional. Ver [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|linguagem|Opcional. O idioma padrão de todos os [ \<cadeias de caracteres >](../extensibility/strings-element.md) elementos na tabela de comandos:<br /><br /> language="en-us"|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|nenhuma.|nenhuma.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos os elementos que representam comandos — ou seja, itens de menu, menus, barras de ferramentas e caixas de combinação — que um VSPackage fornece ao IDE.|  
  
## <a name="example"></a>Exemplo  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    …  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Como os VSPackages adicionam elementos da Interface do usuário](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)
