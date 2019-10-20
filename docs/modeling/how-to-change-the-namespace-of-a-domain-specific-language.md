---
title: 'Como: alterar o namespace de uma linguagem específica de domínio'
ms.date: 10/31/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b64a61c02f44db0ce70b758331d0d70f7bb8014d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653752"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Como: alterar o namespace de uma linguagem específica de domínio

Você pode alterar o namespace de uma linguagem específica de domínio. Faça a alteração no **Gerenciador de DSL**, nas propriedades do projeto de pacote DSL e nas informações do assembly.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Para alterar o namespace de uma linguagem específica de domínio

1. No **Gerenciador de DSL**, selecione o nó **DSL** .

2. Na janela **Propriedades** , altere a propriedade **namespace** .

3. Salve a solução e transforme os modelos.

4. No menu **projeto** , escolha **Propriedades de DSL**.

   As propriedades do seu projeto são exibidas.

5. Selecione a guia **aplicativo** .

6. Altere a propriedade de **namespace padrão** para o novo nome de namespace.

7. Se você também quiser alterar o nome do assembly, altere a propriedade do **nome do assembly.**

8. Se você alterou o nome do assembly, abra DslPackage\Package.tt e atualize esta linha:

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Se você tiver escrito qualquer código personalizado, certifique-se de alterar o namespace e as referências de classe nos arquivos de código.

10. Redefina a instância experimental do Visual Studio.

    1. Exclua **\users \\** _{your name}_ **\AppData\Local\Microsoft\VisualStudio \\ \*Exp**.

    2. No menu **Iniciar** do Windows, escolha **todos os programas**  > **Microsoft Visual Studio 2010 SDK**  > **ferramentas**  > **redefinir a instância experimental**.

11. No menu **Compilar** , escolha **Recompilar solução**.

## <a name="see-also"></a>Consulte também

[Glossário de ferramentas de linguagem específica de domínio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)