# Test Case Login Valid
import com.kms.katalon.core.testobject.TestObject
import com.kms.katalon.core.testobject.ConditionType
import static com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUI

// Helper function (tetap pakai new TestObject di dalam)
def createTestObject(String attr, String value) {
    TestObject to = new TestObject()
    to.addProperty(attr, ConditionType.EQUALS, value)
    return to
}

// Open browser
WebUI.openBrowser('')
WebUI.navigateToUrl('https://example.com/login')

// Put Username
TestObject username = createTestObject('id', 'username')
WebUI.waitForElementVisible(username, 10)
WebUI.setText(username, 'User123')

// Put Password
TestObject password = createTestObject('id', 'password')
WebUI.waitForElementVisible(password, 10)
WebUI.setEncryptedText(password, 'P@ssw0rd')

// CLick Login button
TestObject loginBtn = createTestObject('id', 'login')
WebUI.waitForElementClickable(loginBtn, 10)
WebUI.click(loginBtn)

// Dashboard (indikator sukses)
TestObject dashboard = createTestObject('id', 'dashboard')

// Wait dashboard muncul
WebUI.waitForElementVisible(dashboard, 10)

// Assertion
WebUI.verifyElementVisible(dashboard)

// Close browser
WebUI.closeBrowser()
