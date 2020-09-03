---
title: Instalar um perfil UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, profiles
ms.assetid: 586f9ba5-4d01-4a1d-b001-32e2efaa4f24
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 89531fe0f2e912a6aabd962ab56ca7a24a7f3e20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850660"
---
# <a name="install-a-uml-profile"></a>Instalar um perfil UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode estender o Visual Studio com um perfil UML. Um perfil permite adicionar estereótipos e propriedades adicionais aos elementos que você pode criar em modelos UML. Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Se você receber um modelo UML que foi criado usando perfis, algumas propriedades não serão exibidas, a menos que você instale os mesmos perfis.

 Um perfil é distribuído dentro de uma extensão do Visual Studio. Uma extensão também pode conter outros recursos, como comandos de menu. Para obter mais informações, consulte [Gerenciando extensões do Visual Studio](https://msdn.microsoft.com/library/dd293638(VS.100).aspx).

### <a name="to-install-a-uml-profile-on-your-computer"></a>Para instalar um perfil UML em seu computador

1. O perfil deve ter sido fornecido a você na forma de um arquivo de extensão () do Visual Studio `.vsix` . Pode haver outros recursos no mesmo arquivo.

     Mova o `.vsix` arquivo para um local conveniente no seu computador.

2. Clique duas vezes no `.vsix` arquivo no Windows Explorer (ou no explorador de arquivos) ou abra-o no [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] .

3. Clique em **instalar** na caixa de diálogo que aparece.

4. Para desinstalar ou desabilitar temporariamente a extensão, abra o **Gerenciador de extensões** no menu **ferramentas** .

### <a name="to-uninstall-or-disable-a-profile-extension"></a>Para desinstalar ou desabilitar uma extensão de perfil

1. No menu **ferramentas** do Visual Studio, clique em **Gerenciador de extensões**.

2. Clique na extensão que você deseja remover e, em seguida, clique em **desabilitar** ou **desinstalar**.

## <a name="see-also"></a>Consulte Também
 [Personalizar seu modelo com perfis e estereótipos](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [defina um perfil para estender o UML](../modeling/define-a-profile-to-extend-uml.md)
