---
title: 'Como: alterar o namespace de uma linguagem específica de domínio | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8b61b248876f701e9d5286063f28b4f71d73e18b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671731"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Como alterar o namespace de uma linguagem específica do domínio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode alterar o namespace de uma linguagem específica de domínio. Você deve fazer a alteração no **Gerenciador de DSL**, nas propriedades do projeto de pacote DSL e nas informações do assembly.

### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Para alterar o namespace de uma linguagem específica de domínio

1. No **Gerenciador de DSL**, clique no nó **DSL** .

2. Na janela **Propriedades** , altere a propriedade **namespace** .

3. Salve a solução e transforme os modelos.

4. No menu **projeto** , clique em **Propriedades de DSL**.

     As propriedades do seu projeto são exibidas.

5. Clique na guia **Aplicativo**.

6. Altere a propriedade de **namespace padrão** para o novo nome de namespace.

7. Se você também quiser alterar o nome do assembly, altere a propriedade do **nome do assembly.**

8. Se você alterou o nome do assembly, abra DslPackage\Package.tt e atualize esta linha:

     `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Se você tiver escrito qualquer código personalizado, certifique-se de alterar o namespace e as referências de classe nos arquivos de código.

10. Redefina a instância experimental do Visual Studio.

    1. Excluir **\Users \\ **_{Your Name}_**\AppData\Local\Microsoft\VisualStudio \\ \* exp**

    2. No menu **Iniciar** do Windows, escolha **todos os programas**, **Microsoft Visual Studio SDK 2010**, **ferramentas**, **redefinir a instância experimental**.

11. No menu **Compilar** , escolha **Recompilar solução**.

## <a name="see-also"></a>Consulte Também
 [Glossário das Ferramentas de Linguagem Específica de Domínio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
