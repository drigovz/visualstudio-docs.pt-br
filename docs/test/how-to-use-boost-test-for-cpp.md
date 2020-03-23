---
title: Como usar o Boost.Test para C++
description: Use o Boost.Test para criar testes de unidade no Visual Studio.
ms.date: 01/29/2020
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 0a1a621c7ee7175d86b2cbcf9a6e2c02c0aecbb3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76922918"
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Como usar o Boost.Test para C++ no Visual Studio

No Visual Studio 2017 e posteriormente, o adaptador de teste Boost.Test é integrado ao Visual Studio IDE. É um componente do desenvolvimento do Desktop com carga de trabalho **C++.**

![Adaptador de Teste para Boost.Test](media/cpp-boost-component.png)

Se você não tiver a carga de trabalho **Desenvolvimento para desktop com C++** instalada, abra o **Instalador do Visual Studio**. Selecione a carga de trabalho **Desenvolvimento para desktop com C++** e escolha o botão **Modificar**.

## <a name="install-boost"></a>Instalar o Boost

O Boost.Test exige o [Boost](https://www.boost.org/)! Se você não tiver o Boost instalado, recomendamos que você use o gerenciador de pacotes Vcpkg.

1. Siga as instruções em [Vcpkg: um gerenciador de pacotes C++ para Windows](/cpp/vcpkg) para instalar vcpkg (se você ainda não o tiver).

1. Instale a biblioteca Boost.Test dinâmica ou estática:

    - Execute `vcpkg install boost-test` para instalar a biblioteca Boost.Test dinâmica.

       -OU-

    - Execute `vcpkg install boost-test:x86-windows-static` para instalar a biblioteca Boost.Test estática.

1. Execute `vcpkg integrate install` para configurar o Visual Studio com a biblioteca e incluir caminhos para os cabeçalhos e os binários do Boost.

Você tem uma escolha em como configurar seus testes dentro de sua solução no Visual Studio: Você pode incluir seu código de teste no projeto em teste, ou pode criar um projeto de teste separado para seus testes. Ambas as escolhas têm vantagens e desvantagens.

## <a name="add-tests-inside-your-project"></a>Adicione testes dentro do seu projeto

No Visual Studio 2017 versão 15.6 e posterior, você pode adicionar um modelo de item para testes em seu projeto. Ambos os testes e seu código vivem no mesmo projeto. Você terá que criar uma configuração de compilação separada para gerar uma compilação de teste. E, você vai precisar manter os testes fora de sua depuração e liberar builds.

No Visual Studio 2017 versão 15.5, não há nenhum modelo de projeto de teste ou de item pré-configurado disponível para o Boost.Test. Use as instruções para criar e configurar um projeto de teste separado.

### <a name="create-a-boosttest-item"></a>Criar um item Boost.Test

1. Para criar um arquivo *.cpp* para seus testes, clique com o botão direito do mouse no nó do projeto no **Solution Explorer** e escolha **Adicionar** > **novo item**.

1. Na caixa de diálogo **Adicionar novo item,** **expanda** > o teste**Visual C++** > **instalado.** Selecione **Boost.Test,** em seguida, escolha **Adicionar** para adicionar *Test.cpp* ao seu projeto.

   ![Modelo de item Boost.Test](media/boost_test_item_template.png)

O novo arquivo *Test.cpp* contém um método de teste de amostra. Este arquivo é onde você pode incluir seus próprios arquivos de cabeçalho e escrever testes para o seu aplicativo.

O arquivo de teste também usa `main` macros para definir uma nova rotina para configurações de teste. Se você construir seu projeto agora, verá um erro lNK2005, como "_main já definido em main.obj".

### <a name="create-and-update-build-configurations"></a>Criar e atualizar configurações de compilação

1. Para criar uma configuração de teste, na barra de menus, selecione **Build** > **Configuration Manager**. Na caixa de diálogo **Gerenciador de** configuração, abra o dropdown na **configuração da solução Ativa** e escolha **Novo**. Na **caixa de diálogo Configuração** nova solução, digite um nome como "Debug UnitTests". Em **Copiar configurações de** Selecionar **Depuração**e, em seguida, escolha **OK**.

1. Exclua o código de teste das configurações Depuração e Liberação: No **Solution Explorer,** clique com o botão direito do mouse em Test.cpp e selecione **Propriedades**. Na **caixa de diálogo Páginas** de propriedade, selecione **Todas as configurações** na estava em evasão de **configuração.** Selecione **Propriedades de configuração** > **geral** e abra a isto para a **propriedade Excluídos da compilação.** Selecione **Sim,** em seguida, escolha **Aplicar** para salvar suas alterações.

1. Para incluir o código de teste na configuração Debug UnitTests, na caixa de diálogo **Páginas de propriedade,** selecione **Depuração UnitTests** na série **de sibilização Configuração.** Selecione **Não** na propriedade **Excluídos da compilação** e escolha **OK** para salvar suas alterações.

1. Exclua o código principal da configuração Debug UnitTests. No **Solution Explorer,** clique com o `main` botão direito do mouse no arquivo que contém sua função e selecione **Propriedades**. Na **caixa de diálogo Páginas** de propriedade, selecione **Depurar UnidadesTestes** na **parada de configuração.** Selecione **Propriedades de configuração** > **geral** e abra a isto para a **propriedade Excluídos da compilação.** Selecione **Sim,** em seguida, escolha **OK** para salvar suas alterações.

1. Defina a configuração da solução **para Depurar UnitTests**e crie seu projeto para permitir que o **Test Explorer** descubra o método.

Desde que o nome de configuração criado comece com as palavras "Depurar" ou "Liberar", as bibliotecas boost.test correspondentes são captadas automaticamente.

O modelo de item usa a variante de cabeçalho único do Boost.Test, mas você pode modificar o caminho #include a fim de usar a variante de biblioteca autônoma. Para saber mais, confira [Adicionar diretivas de inclusão](#add-include-directives).

## <a name="create-a-separate-test-project"></a>Crie um projeto de teste separado

Em muitos casos, é mais fácil usar um projeto separado para seus testes. Você não terá que criar uma configuração de teste especial para o seu projeto. Ou, exclua arquivos de teste de compilações Debug e Release.

### <a name="to-create-a-separate-test-project"></a>Para criar um projeto de teste separado

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó da solução e escolha **Adicionar** > **Novo Projeto**.

1. No **Adicionar um novo diálogo** de projeto, escolha **C++**, **Windows**e **Console** nas gotas do filtro. Selecione o modelo **do aplicativo de console** e escolha **Next**.

1. Dê um nome ao projeto e escolha **Criar**.

1. Exclua `main` a função no arquivo *.cpp.*

1. Se você estiver usando a versão de biblioteca dinâmica ou de um único cabeçalho do Boost.Test, vá para [Adicionar diretivas](#add-include-directives)incluir . Se você estiver usando a versão da biblioteca estática, então você tem que fazer alguma configuração adicional:

   a. Para editar o arquivo de projeto, primeiro descarregue-o. No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó do projeto e escolha **Descarregar Projeto**. Em seguida, clique com o botão direito do mouse no nó do projeto e escolha **Editar <name\>.vcxproj**.

   b. Adicione duas linhas no grupo de propriedades **Globais**, como é mostrado aqui:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```

   c. Salve e feche o * \*arquivo .vcxproj* e, em seguida, recarregue o projeto.

   d. Para abrir a **Páginas de Propriedades**, clique com o botão direito do mouse no nó do projeto e escolha **Propriedades**.

   e. Expanda a geração de código **C/C++** > **Code Generation**e selecione **A Biblioteca de Tempo de Execução**. Selecione **/MTd** para depurar a biblioteca de runtime estática ou **/MT** para liberar a biblioteca de runtime estática.

   f. Expandir **o sistema de linker** > **System**. Verificar **que o SubSystem** está definido como **Console**.

   g. Escolha **OK** para fechar as páginas de propriedades.

## <a name="add-include-directives"></a>Adicionar diretivas de inclusão

1. No arquivo *teste .cpp,* `#include` adicione as diretivas necessárias para tornar os tipos e funções do programa visíveis ao código de teste. Se você estiver usando um projeto de teste separado, normalmente, o programa está em um nível de irmão na hierarquia da pasta. Se você digitar `#include "../"`, uma janela do IntelliSense será exibida e permitirá que você selecione o caminho completo para o arquivo de cabeçalho.

   ![Adicionar diretivas de #inclusão](media/cpp-gtest-includes.png)

   Você pode usar a biblioteca autônoma com:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   Ou, use a versão de cabeçalho único com:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Em seguida, defina `BOOST_TEST_MODULE`.

O exemplo a seguir é suficiente para que o teste seja detectável no **Gerenciador de Testes**:

```cpp
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp\> //single-header
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my_boost_test)
{
    std::string expected_value = "Bill";

    // assume MyClass is defined in MyClass.h
    // and get_value() has public accessibility
    MyClass mc;
    BOOST_CHECK(expected_value == mc.get_value());
}
```

## <a name="write-and-run-tests"></a>Gravar e executar testes

Agora, você está pronto para escrever e executar testes do Boost. Consulte a [documentação](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html) da biblioteca de testes Boost para obter informações sobre as macros de teste. Consulte [Executar testes de unidade com o Gerenciador de Testes](run-unit-tests-with-test-explorer.md) para saber mais sobre como descobrir, executar e agrupar testes usando o **Gerenciador de Testes**.

## <a name="see-also"></a>Confira também

- [Escrever testes de unidade para C/C++](writing-unit-tests-for-c-cpp.md)
