---
title: Erros da política de análise do código
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac7a949b3f8a1e0c9d44c6194f87745b4e3f17a8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587739"
---
# <a name="code-analysis-policy-errors"></a>Erros da política de análise do código

Os seguintes erros ocorrerão se a política de análise de código não for satisfeita no check-in:

**As configurações de análise de código para um ou mais projetos não são compatíveis com a política de análise de código.**

Os requisitos de análise de código que verificam o controle do código-fonte do projeto não foram atendidos para um ou mais projetos de código. Esse erro pode ser causado por uma ou mais das seguintes condições:

- A análise de código não está habilitada na compilação para todos os projetos na solução.

- O conjunto de regras locais para o projeto no Visual Studio tem uma configuração de **ação** menos restritiva do que o conjunto de regras do projeto, por exemplo, uma regra definida como **ação**=**erro** no servidor tem sua **ação** definida como **aviso** ou **nenhum** no conjunto de regras que está sendo executado no Visual Studio).

- O conjunto de regras especificado no Visual Studio não contém todas as regras especificadas no conjunto de regras especificado na política de check-in de análise de código do projeto.

**Falha na política de análise de código. Há erros no projeto {0} ou a compilação não está atualizada.**

A compilação contém erros ou os erros foram corrigidos, mas a análise de código não foi executada após a correção.

**Falha no check-in. A política de análise de código requer que você faça o check-in por meio do Visual Studio com uma solução aberta.**

A política de análise de código requer que todos os arquivos que estão sendo verificados devem estar na solução aberta no momento. Para corrigir esse erro, abra a solução que contém o arquivo no qual será feito o check-in.

**Nem todos os arquivos no check-in pendente estão dentro da solução aberta no momento.**

A política de análise de código requer que todos os arquivos que estão sendo verificados devem estar na solução aberta no momento. Esse erro é gerado quando há uma solução aberta, mas alguns arquivos na exibição "verificação pendente" não fazem parte da solução atualmente aberta. Para corrigir esse erro, abra a solução que contém o arquivo no qual será feito o check-in.

**A versão de '{0}' não está correta. O nome forte especificado na política é '{1}'.**

Este erro se aplica a projetos .NET. Uma Rule. dll exigida pela política de análise de código existe no computador local, mas a versão/chave pública não corresponde. Para corrigir esse erro, o criador da política deve atualizar o. DLLs em *C:\Program Files\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules\\* Directory em seu computador.

**o assembly '{0}' especificado na política não existe.**

Este erro se aplica a projetos .NET. Uma regra exigida pela política de análise de código não tem a dll correspondente instalada no computador cliente. Para corrigir esse erro, o criador de política deve atualizar a dll em *C:\Program Files\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules\\* Directory em seu computador.

**As configurações de regra de {0} de projeto não estão em conformidade com a política de análise de código.**

Este erro se aplica a projetos .NET. As configurações de regras de código gerenciado não são tão rigorosas quanto a política requer. Para corrigir esse erro, a configuração do cliente deve ser a mesma ou mais estrita do que o requisito de política no servidor.

**A análise de código não está habilitada na configuração ativa. Alterne para a configuração {0} e compilar o projeto {1} antes de fazer check-in.**

No [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], a configuração ativa não tem a análise de código habilitada, mas há pelo menos uma análise de código habilitada.

**Você deve habilitar a análise de código para binários gerenciados no projeto {0} Propriedades e compilar antes de fazer check-in.**

Esse erro se aplica a aplicativos [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] .NET. A política requer que a análise de código gerenciado seja executada, mas não está habilitada no projeto atual no cliente.

**Você deve habilitar a análise de código no Project {0} Propriedades e compilar antes de fazer check-in.**

Esse erro é aplicado a projetos de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e projetos Web. A política requer que a análise de código gerenciado seja executada, mas não está habilitada no projeto atual no cliente.

**Você deve habilitar a análiseC++ de C/Code nas propriedades do projeto {0} e compilar antes de fazer check-in.**

Esse erro se aplica a projetos não gerenciados. A política de análise de código requer análise de códigoC++para C/, mas não está habilitada no projeto atual no cliente.

## <a name="see-also"></a>Veja também

- [Erros de aplicativo de análise de código](../code-quality/code-analysis-application-errors.md)
