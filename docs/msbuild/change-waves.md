---
title: Alterar ondas
description: Saiba como habilitar ou desabilitar recursos no MSBuild que são potencialmente perturbadores.
ms.date: 11/10/2020
ms.topic: conceptual
helpviewer_keywords:
- Change waves [MSBuild]
- MSBuildDisableFeaturesFromVersion environment variable
author: ghogen
ms.author: ghogen
manager: jillfra
monikerRange: '>=vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 68aafd8ebb97b4bf649cc41eb7739e1700c9cb1a
ms.sourcegitcommit: 83a39d48b00c6c351e5c1707942633b7f73aaad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94532065"
---
# <a name="change-waves"></a>Alterar ondas

Uma *onda de alteração* é um conjunto de alterações de comportamento no MSBuild que você pode recusar especificando um sinalizador específico como uma variável de ambiente. A finalidade disso é avisar sobre alterações potencialmente perturbadoras para que você tenha flexibilidade na adaptação a essas alterações antes que elas se tornem funcionalidades padrão. Todos os recursos em uma onda de alteração específica só podem ser habilitados ou desabilitados juntos, não individualmente.

Quando você atualiza para uma nova versão do MSBuild, as alterações que são potencialmente quebras são habilitadas por padrão, mas se um recurso afetar sua compilação negativamente, você poderá desabilitar facilmente essa onda de alterações. Cada onda de alteração é identificada por um número de versão do MSBuild (por exemplo, 16,8), mas a definição da onda de alteração controla apenas determinados recursos que têm o potencial de afetar o processo de compilação, e não todas as alterações nessa versão do MSBuild. Uma lista dos recursos em cada onda de alteração aparece [mais adiante neste artigo](#change-waves-and-associated-features). Desabilitar uma alteração de onda também desabilita as ondas de alteração de versões superiores.

## <a name="opt-out-of-change-wave-features"></a>Recusar recursos de onda de alteração

Para desabilitar os recursos em uma alteração de onda, defina a variável de ambiente `MSBuildDisableFeaturesFromVersion` para a alteração de onda (ou a versão do MSBuild) que contém o recurso que você deseja **desabilitar**. Esta é a versão do MSBuild para a qual os recursos foram desenvolvidos. Consulte o mapeamento de ondas de alteração para os recursos abaixo.

### <a name="msbuilddisablefeaturesfromversion-values"></a>Valores de MSBuildDisableFeaturesFromVersion

Você receberá um aviso e/ou padrão para uma onda específica se não definir `MSBuildDisableFeaturesFromVersion` como uma onda de alteração válida. A tabela a seguir mostra as configurações possíveis:

| Valor `MSBuildDisableFeaturesFromVersion`                         | Resultado        | Receber aviso? |
| :-------------                                                    | :----------   | :----------: |
| Definição                                                             | Habilitar todas as ondas de alteração, o que significa que todos os recursos atrás de cada onda de alteração estão habilitados.               | No   |
| Qualquer onda de alteração válida e atual (por exemplo, `16.8` )                      | Desabilite todos os recursos atrás da alteração Wave `16.8` **e superior**.                                           | No   |
| Valor inválido (por exemplo, `16.9` quando as ondas válidas são `16.8` e `16.10` )| O padrão é o valor válido mais próximo (em ordem crescente). Por exemplo, `16.9` a configuração vai padronizar você para `16.10` .               | No   |
| Fora de rotação (por exemplo, `17.1` quando a onda mais alta é `17.0` )      | Fixe para o valor válido mais próximo. Por exemplo, `17.1` coloca para `17.0` e `16.5` coloca para `16.8`                    | Yes  |
| Formato inválido (por exemplo, `16x8` , `17_0` `garbage` )                    | Habilitar todas as ondas de alteração, o que significa que todos os recursos atrás de cada onda de alteração estão habilitados.               | Yes  |

## <a name="change-waves-and-associated-features"></a>Alterar ondas e recursos associados

Os links na lista abaixo vão para o GitHub PR para o recurso.

### <a name="168"></a>16,8

- [Habilitar nowarn](https://github.com/dotnet/msbuild/pull/5671)
- [Truncar mensagens de log ignoradas de destino/tarefa para 1024 caracteres](https://github.com/dotnet/msbuild/pull/5553)
- [Não expanda a unidade completa globs com condição falsa](https://github.com/dotnet/msbuild/pull/5669)

### <a name="1610"></a>16.10

- [Erro quando uma expansão de propriedade em uma condição tem espaço em branco](https://github.com/dotnet/msbuild/pull/5672)

### <a name="170"></a>17.0

Ainda não há entradas nesse Wave de alteração.

## <a name="change-waves-that-are-out-of-rotation"></a>Alterar as ondas que estão fora de rotação

Não há nenhuma ondas de alteração de rotação no momento.

## <a name="faq"></a>Perguntas frequentes

**Por que ter como alvo todas as outras versões para girar as ondas de alteração?**

Acreditamos que isso é tempo suficiente para ter discussões com aquelas afetadas e auxiliar na adaptação às alterações.

**Por que uma variável de ambiente e não uma propriedade de projeto?**

Há cenários em que queremos posicionar um recurso em uma onda de alteração antes que o MSBuild tenha carregado o projeto. Por esse motivo, as ondas de alteração exigem o uso de variáveis de ambiente.

**Por que recusar a aceitação?**

A recusa é uma abordagem melhor para nós; caso contrário, provavelmente receberemos Comentários limitados quando um recurso impactar as compilações dos clientes.

## <a name="see-also"></a>Confira também

- [MSBuild](msbuild.md)
- [O que há de novo no MSBuild 16](whats-new-msbuild-16-0.md)
