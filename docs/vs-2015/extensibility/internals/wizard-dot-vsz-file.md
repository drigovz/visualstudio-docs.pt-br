---
title: Assistente (. Arquivo de vsz) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab1adde4c7018f136f47769e16a8ce2fedf72c93
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687658"
---
# <a name="wizard-vsz-file"></a>Arquivo do assistente (.Vsz)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O IDE (ambiente de desenvolvimento integrado) usa arquivos. vsz para iniciar os assistentes. Esses arquivos. vsz contêm informações que o IDE usa para determinar qual assistente deve ser chamado e quais informações passar para o assistente.  
  
 Um arquivo. vsz é uma versão de um arquivo de texto formatado. ini que não tem seções. As informações conhecidas para o IDE são armazenadas no início do arquivo. Isso fornece um link entre o assistente que o IDE chama e os parâmetros que estão no arquivo. vsz a serem passados para o IDE. O restante do arquivo fornece parâmetros que são específicos para o assistente e que devem ser coletados pelo IDE e passados para o assistente específico.  
  
 O exemplo a seguir mostra o conteúdo de um arquivo. vsz.  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 A seguir estão as partes no arquivo. vsz.  
  
|Parte|Descrição|  
|----------|-----------------|  
|VSWizard|O primeiro parâmetro no arquivo é o número de versão do formato de arquivo de modelo. Esse número de versão deve ser 6,0, 7,0, 7,1 ou 8,0. Não é possível iniciar outros números e causar um erro de formato inválido.|  
|Assistente|Este campo contém o ProgID de OLE do assistente ou, como alternativa, uma representação de cadeia de caracteres de GUID do CLSID do assistente que é Cocriado pelo IDE.|  
|Param|Essas partes são opcionais. Você pode adicionar tantos quantos forem necessários.|  
  
 Os parâmetros permitem que o arquivo. vsz passe parâmetros personalizados adicionais para o assistente. Cada valor é passado como um elemento string em uma matriz de variantes para o assistente. Para obter mais informações, consulte [Custom Parameters](../../extensibility/internals/custom-parameters.md). Para obter informações sobre como usar um arquivo. vsz no desenvolvimento de assistentes personalizados, consulte [. Arquivo vsz (controle de projeto)](https://msdn.microsoft.com/library/b8678fee-6795-46d1-9338-48b22d5e9207)  
  
 Para adicionar uma ID de localidade padrão ao seu arquivo. vsz, especifique `FALLBACK_LCID` = xxxx, onde xxxx é a ID de localidade, por exemplo, 1033 para inglês. Quando `FALLBACK_LCID` o parâmetro for definido, o assistente usará a ID de localidade de fallback fornecida se a ID atual não for encontrada.  
  
## <a name="see-also"></a>Consulte Também  
 [Parâmetros personalizados](../../extensibility/internals/custom-parameters.md)   
 [Assistentes](../../extensibility/internals/wizards.md)   
 [Arquivos de descrição do diretório de modelo (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
