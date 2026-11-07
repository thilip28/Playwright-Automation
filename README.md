# Playwright-Automation
Interview testing
const { test, expect } = require('@playwright/test');

test('Amazon Login Test', async ({ page }) => {

    // Navigate to Amazon
    await page.goto('https://www.amazon.in/');

    // Click Sign In
    await page.getByRole('link', { name: /sign in/i }).first().click();

    // Enter Email
    await page.locator('#ap_email')
        .fill(process.env.AMAZON_EMAIL);
//--------------//
    // Click Continue
    await page.locator('#continue').click();

    // Enter Password
    await page.locator('#ap_password')
        .fill(process.env.AMAZON_PASSWORD);

    // Click Sign In
    await page.locator('#signInSubmit').click();

    // Verify successful login
    await expect(page.locator('#nav-link-accountList'))
        .toContainText(/account/i);

});
