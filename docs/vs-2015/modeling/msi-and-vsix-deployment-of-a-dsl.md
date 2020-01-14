---
title: Implantação de VSIX de uma DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: be9d3d44bfceaae1f2912086c3d20c90ce1e094b
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916554"
---
# <a name="vsix-deployment-of-a-dsl"></a>Implantação do VSIX de uma DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode instalar uma linguagem específica de domínio em seu próprio computador ou em outros computadores. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] já deve estar instalado no computador de destino.

## <a name="Installing"></a>Instalando e desinstalando uma DSL usando o VSX
 Quando o DSL é instalado por esse método, o usuário pode abrir um arquivo DSL no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], mas o arquivo não pode ser aberto no Windows Explorer.

#### <a name="to-install-a-dsl-by-using-the-vsix"></a>Para instalar uma DSL usando o VSIX

1. Em seu computador, localize o arquivo **. vsix** criado por seu projeto de pacote DSL.

    1. No **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **DslPackage** e clique em **abrir pasta no Windows Explorer**.

    2. Localize o arquivo **bin\\\*\\** _seuprojeto_ **. DslPackage. vsix**

2. Copie o arquivo **. vsix** para o computador de destino no qual você deseja instalar a DSL. Este pode ser seu próprio computador ou outro.

    - O computador de destino deve ter uma das edições do [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] que dá suporte a DSLs em tempo de execução. Para obter mais informações, consulte [supported Visual Studio Editions for visualization & Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

    - O computador de destino deve ter uma das edições do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] especificado em **DslPackage\source.Extensions.manifest**.

3. No computador de destino, clique duas vezes no arquivo **. vsix** .

     O **instalador de extensão do Visual Studio** é aberto e instala a extensão.

4. Inicie ou reinicie o [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

5. Para testar a DSL, use [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para criar um novo arquivo que tenha a extensão que você definiu para a sua DSL.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Para desinstalar uma DSL que foi instalada usando o VSX

1. No menu **ferramentas** , clique em **Gerenciador de extensões**.

2. Expanda **extensões instaladas**.

3. Selecione a extensão na qual a DSL está definida e clique em **desinstalar**.

   Raramente, uma extensão defeituosa não carrega e cria um relatório na janela de erro, mas não aparece no Gerenciador de extensões. Nesse caso, você pode remover a extensão excluindo o arquivo de:

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**
