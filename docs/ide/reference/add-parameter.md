---
title: Adicionar parâmetro a uma ação rápida de método
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: da435d5bf4e0b7239b984263838c275d3b5c9ab3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920213"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Adicionar um parâmetro a um método usando uma Ação Rápida

Esta geração de código aplica-se a:

- C#

- Visual Basic

**O quê:** Permite adicionar automaticamente um parâmetro a um método com base no uso.

**Quando:** Você precisa adicionar um parâmetro a um método e deseja declará-lo automaticamente.

**Por que:** Você poderia adicionar o parâmetro para a declaração do método antes de chamá-lo, no entanto, esse recurso adiciona o parâmetro automaticamente com base na chamada de método.

## <a name="how-to-use-it"></a>Como usá-lo

1. Adicione um argumento extra a uma chamada de método.

   Uma linha vermelha "ondulada" aparece sob o nome do método onde você o chama.

2. Coloque o ponteiro sobre a linha vermelha "ondulada" até aparecer o menu Ações rápidas. Selecione a **seta para baixo** no menu Ações Rápidas e, em seguida, selecione **Adicionar parâmetro ao [método]**.

   ![Adicionar parâmetro a ação rápida de método no Visual Studio](media/add-parameter-to-method.png)

   > [!TIP]
   > Também é possível acessar o menu Ações Rápidas colocando o cursor na linha de chamada de método e, em seguida, pressionando a tecla **Ctrl**+**.** ou selecionando o ícone de lâmpada na margem de arquivo.

   O Visual Studio adiciona o novo parâmetro à declaração de método.

> [!NOTE]
> Se você tiver outras chamadas para o método, elas podem produzir erros depois de usar essa Ação Rápida porque não especificam um argumento para o parâmetro recém-adicionado.

## <a name="see-also"></a>Consulte também

- [Adicionar parâmetro ao construtor](generate-constructor.md#addparameter)