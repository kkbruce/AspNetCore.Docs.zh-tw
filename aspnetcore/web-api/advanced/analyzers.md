---
title: 使用 Web API 分析器
author: pranavkm
description: 深入了解 Microsoft.AspNetCore.Mvc.Api.Analyzers 中的 Web API 分析器。
monikerRange: '>= aspnetcore-2.2'
ms.author: pranavkm
ms.custom: mvc
ms.date: 11/13/2018
uid: web-api/advanced/analyzers
ms.openlocfilehash: 89424d89ec2b3125fd3c6b7c86fed2d292b153e6
ms.sourcegitcommit: f202864efca81a72ea7120c0692940c40d9d0630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2018
ms.locfileid: "51635380"
---
# <a name="use-web-api-analyzers"></a><span data-ttu-id="66be1-103">使用 Web API 分析器</span><span class="sxs-lookup"><span data-stu-id="66be1-103">Use web API analyzers</span></span>

<span data-ttu-id="66be1-104">ASP.NET Core 2.2 推出包含 Web API 分析器的 [Microsoft.AspNetCore.Mvc.Api.Analyzers](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Api.Analyzers) NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="66be1-104">ASP.NET Core 2.2 introduces the [Microsoft.AspNetCore.Mvc.Api.Analyzers](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Api.Analyzers) NuGet package containing analyzers for web APIs.</span></span> <span data-ttu-id="66be1-105">在建置 [API 慣例](xref:web-api/advanced/conventions)時，分析器使用以 <xref:Microsoft.AspNetCore.Mvc.ApiControllerAttribute> 標註的控制器。</span><span class="sxs-lookup"><span data-stu-id="66be1-105">The analyzers work with controllers annotated with <xref:Microsoft.AspNetCore.Mvc.ApiControllerAttribute>, while building on [API conventions](xref:web-api/advanced/conventions).</span></span>

## <a name="package-installation"></a><span data-ttu-id="66be1-106">套件安裝</span><span class="sxs-lookup"><span data-stu-id="66be1-106">Package installation</span></span>

<span data-ttu-id="66be1-107">可使用下列方法新增 `Microsoft.AspNetCore.Mvc.Api.Analyzers`：</span><span class="sxs-lookup"><span data-stu-id="66be1-107">`Microsoft.AspNetCore.Mvc.Api.Analyzers` can be added with one of the following approaches:</span></span>

### <a name="visual-studiotabvisual-studio"></a>[<span data-ttu-id="66be1-108">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="66be1-108">Visual Studio</span></span>](#tab/visual-studio)

* <span data-ttu-id="66be1-109">從 [套件管理員主控台] 視窗中：</span><span class="sxs-lookup"><span data-stu-id="66be1-109">From the **Package Manager Console** window:</span></span>
  * <span data-ttu-id="66be1-110">移至 [檢視] > [其他視窗] > [套件管理員主控台]。</span><span class="sxs-lookup"><span data-stu-id="66be1-110">Go to **View** > **Other Windows** > **Package Manager Console**.</span></span>
  * <span data-ttu-id="66be1-111">巡覽至 *ApiConventions.csproj* 檔案所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="66be1-111">Navigate to the directory in which the *ApiConventions.csproj* file exists.</span></span>
  * <span data-ttu-id="66be1-112">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="66be1-112">Execute the following command:</span></span>

    ```powershell
    Install-Package Microsoft.AspNetCore.Mvc.Api.Analyzers
    ```

* <span data-ttu-id="66be1-113">從 [管理 NuGet 套件] 對話方塊中：</span><span class="sxs-lookup"><span data-stu-id="66be1-113">From the **Manage NuGet Packages** dialog:</span></span>
  * <span data-ttu-id="66be1-114">在 [方案總管] > [管理 NuGet 套件] 中，以滑鼠右鍵按一下專案。</span><span class="sxs-lookup"><span data-stu-id="66be1-114">Right-click the project in **Solution Explorer** > **Manage NuGet Packages**.</span></span>
  * <span data-ttu-id="66be1-115">將 [套件來源] 設定為 "nuget.org"。</span><span class="sxs-lookup"><span data-stu-id="66be1-115">Set the **Package source** to "nuget.org".</span></span>
  * <span data-ttu-id="66be1-116">在搜尋方塊中輸入 "Microsoft.AspNetCore.Mvc.Api.Analyzers"。</span><span class="sxs-lookup"><span data-stu-id="66be1-116">Enter "Microsoft.AspNetCore.Mvc.Api.Analyzers" in the search box.</span></span>
  * <span data-ttu-id="66be1-117">從 [瀏覽] 索引標籤中選取 "Microsoft.AspNetCore.Mvc.Api.Analyzers" 套件，並按一下 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="66be1-117">Select the "Microsoft.AspNetCore.Mvc.Api.Analyzers" package from the **Browse** tab and click **Install**.</span></span>

### <a name="visual-studio-for-mactabvisual-studio-mac"></a>[<span data-ttu-id="66be1-118">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="66be1-118">Visual Studio for Mac</span></span>](#tab/visual-studio-mac)

* <span data-ttu-id="66be1-119">在 [Solution Pad] > [新增套件...] 中，以滑鼠右鍵按一下 [套件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="66be1-119">Right-click the *Packages* folder in **Solution Pad** > **Add Packages...**.</span></span>
* <span data-ttu-id="66be1-120">將 [新增套件] 視窗的 [來源] 下拉式清單設定為 "nuget.org"。</span><span class="sxs-lookup"><span data-stu-id="66be1-120">Set the **Add Packages** window's **Source** drop-down to "nuget.org".</span></span>
* <span data-ttu-id="66be1-121">在搜尋方塊中輸入 "Microsoft.AspNetCore.Mvc.Api.Analyzers"。</span><span class="sxs-lookup"><span data-stu-id="66be1-121">Enter "Microsoft.AspNetCore.Mvc.Api.Analyzers" in the search box.</span></span>
* <span data-ttu-id="66be1-122">從結果窗格中選取 "Microsoft.AspNetCore.Mvc.Api.Analyzers" 套件，然後按一下 [新增套件]。</span><span class="sxs-lookup"><span data-stu-id="66be1-122">Select the "Microsoft.AspNetCore.Mvc.Api.Analyzers" package from the results pane and click **Add Package**.</span></span>

### <a name="visual-studio-codetabvisual-studio-code"></a>[<span data-ttu-id="66be1-123">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="66be1-123">Visual Studio Code</span></span>](#tab/visual-studio-code)

<span data-ttu-id="66be1-124">從 [整合式終端機] 執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="66be1-124">Run the following command from the **Integrated Terminal**:</span></span>

```console
dotnet add ApiConventions.csproj package Microsoft.AspNetCore.Mvc.Api.Analyzers
```

### <a name="net-core-clitabnetcore-cli"></a>[<span data-ttu-id="66be1-125">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="66be1-125">.NET Core CLI</span></span>](#tab/netcore-cli)

<span data-ttu-id="66be1-126">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="66be1-126">Run the following command:</span></span>

```console
dotnet add ApiConventions.csproj package Microsoft.AspNetCore.Mvc.Api.Analyzers
```

---

## <a name="analyzers-for-api-conventions"></a><span data-ttu-id="66be1-127">API 慣例的分析器</span><span class="sxs-lookup"><span data-stu-id="66be1-127">Analyzers for API conventions</span></span>

<span data-ttu-id="66be1-128">Open API 文件包含動作可能傳回的狀態碼及回應型別。</span><span class="sxs-lookup"><span data-stu-id="66be1-128">Open API documents contain status codes and response types that an action may return.</span></span> <span data-ttu-id="66be1-129">在 ASP.NET Core MVC 中，如 <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute> 和 <xref:Microsoft.AspNetCore.Mvc.ProducesAttribute> 等屬性會用以記載動作。</span><span class="sxs-lookup"><span data-stu-id="66be1-129">In ASP.NET Core MVC, attributes such as <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute> and <xref:Microsoft.AspNetCore.Mvc.ProducesAttribute> are used to document an action.</span></span> <span data-ttu-id="66be1-130"><xref:tutorials/web-api-help-pages-using-swagger> 會對記載您的 API 以提供進一步詳細資料。</span><span class="sxs-lookup"><span data-stu-id="66be1-130"><xref:tutorials/web-api-help-pages-using-swagger> goes into further detail on documenting your API.</span></span>

<span data-ttu-id="66be1-131">套件中的其中一個分析器會檢查以 <xref:Microsoft.AspNetCore.Mvc.ApiControllerAttribute> 標註的控制器，並辨識未完全記載其回應的動作。</span><span class="sxs-lookup"><span data-stu-id="66be1-131">One of the analyzers in the package inspects controllers annotated with <xref:Microsoft.AspNetCore.Mvc.ApiControllerAttribute> and identifies actions that don't entirely document their responses.</span></span> <span data-ttu-id="66be1-132">參考下列範例：</span><span class="sxs-lookup"><span data-stu-id="66be1-132">Consider the following example:</span></span>

[!code-csharp[](conventions/sample/Controllers/ContactsController.cs?name=missing404docs&highlight=9)]

<span data-ttu-id="66be1-133">上述動作記載 HTTP 200 成功傳回型別，但未記載 HTTP 404 失敗狀態碼。</span><span class="sxs-lookup"><span data-stu-id="66be1-133">The preceding action documents the HTTP 200 success return type but doesn't document the HTTP 404 failure status code.</span></span> <span data-ttu-id="66be1-134">分析器會回報缺少文件的 HTTP 404 狀態碼作為警告。</span><span class="sxs-lookup"><span data-stu-id="66be1-134">The analyzer reports the missing documentation for the HTTP 404 status code as a warning.</span></span> <span data-ttu-id="66be1-135">提供修正問題的選項。</span><span class="sxs-lookup"><span data-stu-id="66be1-135">An option to fix the problem is provided.</span></span>