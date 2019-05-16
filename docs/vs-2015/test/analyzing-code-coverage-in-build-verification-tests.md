---
title: Analisando a cobertura de código em testes de verificação de build | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 59c07d15-511e-4fd0-b398-bde9d5ed00d9
caps.latest.revision: 10
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1dc7dceeaf94ef94a46da6836fea95ac94e49db7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686450"
---
# <a name="analyzing-code-coverage-in-build-verification-tests"></a>Analisando a cobertura de código em testes de verificação de build
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A análise de cobertura de código no Microsoft Visual Studio mostra quanto de seu código está sendo utilizado por testes automatizados. Para obter mais informações, consulte [Usando cobertura de código para determinar quanto código está sendo testado](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
 Quando você faz check-in de seu código, os testes serão executados no servidor de compilação, juntamente com os outros testes de outros membros da equipe. (Se você ainda não tiver configurado isso, consulte [Executar testes no processo de build](https://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38).) É útil analisar a cobertura de código no serviço de build, pois isso dá o panorama mais atualizado e mais abrangente da cobertura em todo o projeto. Também incluirá os testes automatizados do sistema e outros testes codificados que você normalmente não executa nos computadores de desenvolvimento.  
  
1. No Team Explorer, abra **Compilações** e adicione ou edite uma definição de build.  
  
2. Na página **Processo**, expanda **Testes Automatizados**, **Fonte de Teste**, **Configurações de Execução**. Defina **Tipo de Arquivo de Configurações de Execução** como **Cobertura de Código Habilitada**.  
  
    Se você tiver mais de uma definição de Fonte de Teste, repita essa etapa para cada uma.  
  
   - <em>No entanto, não há nenhum campo chamado **Tipo de Arquivo de Configurações de Execução</em>*.*  
  
      Em **Testes Automatizados**, selecione **Assembly de Teste** e escolha o botão de reticências **[...]** no final da linha. Na caixa de diálogo **Adicionar/Editar Execução de Teste**, em **Test Runner**, selecione **Visual Studio Test Runner**.  
  
   ![Configurar a definição de build para cobertura de código](../test/media/codecoverage-plaincc.png "CodeCoverage plainCC")  
  
   Após a execução do build, os resultados da cobertura de código aparecem no resumo do build.  
  
## <a name="see-also"></a>Consulte também  
 [Usando cobertura de código para determinar quanto código está sendo testado](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
