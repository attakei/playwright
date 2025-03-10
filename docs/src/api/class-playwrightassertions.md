# class: PlaywrightAssertions
* since: v1.17

Playwright gives you Web-First Assertions with convenience methods for creating assertions that will wait and retry until the expected condition is met.

Consider the following example:

```js
import { test, expect } from '@playwright/test';

test('status becomes submitted', async ({ page }) => {
  // ...
  await page.locator('#submit-button').click()
  await expect(page.locator('.status')).toHaveText('Submitted');
});
```

```python async
from playwright.async_api import Page, expect

async def test_status_becomes_submitted(page: Page) -> None:
    # ..
    await page.locator("#submit-button").click()
    await expect(page.locator(".status")).to_have_text("Submitted")
```

```python sync
from playwright.sync_api import Page, expect

def test_status_becomes_submitted(page: Page) -> None:
    # ..
    page.locator("#submit-button").click()
    expect(page.locator(".status")).to_have_text("Submitted")
```

```java
...
import static com.microsoft.playwright.assertions.PlaywrightAssertions.assertThat;

public class TestExample {
  ...
  @Test
  void statusBecomesSubmitted() {
    ...
    page.locator("#submit-button").click();
    assertThat(page.locator(".status")).hasText("Submitted");
  }
}
```

```csharp
using System.Threading.Tasks;
using Microsoft.Playwright.NUnit;
using NUnit.Framework;

namespace PlaywrightTests;

[TestFixture]
public class ExampleTests : PageTest
{
    [Test]
    public async Task StatusBecomesSubmitted()
    {
        await Page.Locator("#submit-button").ClickAsync();
        await Expect(Page.Locator(".status")).ToHaveTextAsync("Submitted");
    }
}
```

Playwright will be re-testing the node with the selector `.status` until fetched Node has the `"Submitted"`
text. It will be re-fetching the node and checking it over and over, until the condition is met or until the timeout is
reached. You can pass this timeout as an option.

By default, the timeout for assertions is set to 5 seconds.

## method: PlaywrightAssertions.expectAPIResponse
* since: v1.18
* langs:
  - alias-java: assertThat
  - alias-python: expect
  - alias-js: expect
  - alias-csharp: Expect
- returns: <[APIResponseAssertions]>

Creates a [APIResponseAssertions] object for the given [APIResponse].

```java
PlaywrightAssertions.assertThat(response).isOK();
```

### param: PlaywrightAssertions.expectAPIResponse.response
* since: v1.18
- `response` <[APIResponse]>

[APIResponse] object to use for assertions.

## method: PlaywrightAssertions.expectLocator
* since: v1.18
* langs:
  - alias-java: assertThat
  - alias-python: expect
  - alias-js: expect
  - alias-csharp: Expect
- returns: <[LocatorAssertions]>

Creates a [LocatorAssertions] object for the given [Locator].

```java
PlaywrightAssertions.assertThat(locator).isVisible();
```

```csharp
await Expect(locator).ToBeVisibleAsync();
```

### param: PlaywrightAssertions.expectLocator.locator
* since: v1.18
- `locator` <[Locator]>

[Locator] object to use for assertions.

## method: PlaywrightAssertions.expectPage
* since: v1.18
* langs:
  - alias-java: assertThat
  - alias-python: expect
  - alias-js: expect
  - alias-csharp: Expect
- returns: <[PageAssertions]>

Creates a [PageAssertions] object for the given [Page].

```java
PlaywrightAssertions.assertThat(page).hasTitle("News");
```

```csharp
await Expect(page).ToHaveTitleAsync("News");
```

### param: PlaywrightAssertions.expectPage.page
* since: v1.18
- `page` <[Page]>

[Page] object to use for assertions.

## method: PlaywrightAssertions.setDefaultAssertionTimeout
* since: v1.25
* langs: java

Changes default timeout for Playwright assertions from 5 seconds to the specified value.

```java
PlaywrightAssertions.setDefaultAssertionTimeout(30_000);
```

### param: PlaywrightAssertions.setDefaultAssertionTimeout.timeout
* since: v1.25
- `timeout` <[float]>

Timeout in milliseconds.
