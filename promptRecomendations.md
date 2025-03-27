Okay, let's craft some advice on how to write *effective user prompts* (your questions/requests) that leverage the capabilities of the "Expert AI Android Code Reviewer" system prompt you have. The key is to guide the AI precisely to get the high-quality, strict analysis you desire.

**General Principles:**

1.  **Be Specific, Not Vague:** Avoid overly broad questions like "Is this code good?" or "Find bugs." The AI works best when directed.
2.  **Leverage File Context:** Explicitly mention the file paths (`app/src/.../MyFile.kt`) you want the AI to focus on or relate. This helps it navigate the provided code dump.
3.  **State Your Goal Clearly:** What *kind* of analysis do you want? Bug finding? Performance review? Best practice check? Refactoring ideas? Architectural feedback?
4.  **Focus on Areas of Concern:** If you have specific suspicions (e.g., about threading, state management, lifecycle), point the AI towards them.
5.  **Reference Android Concepts:** Use terms the AI understands (ViewModel, Composable, CoroutineScope, Hilt module, main thread, recomposition, etc.).

**Effective Prompting Strategies & Examples:**

**(Assume you've already pasted the code block gathered by the script)**

1.  **Targeted Bug Hunt:**
    *   *Less Effective:* "Find bugs in the login code."
    *   *More Effective:* "Review `LoginViewModel.kt` and `AuthRepository.kt`. Identify potential race conditions, error handling issues, or incorrect Coroutine scope usage related to the `loginUser` flow."
    *   *Even Better:* "In `UserSessionManager.kt`, I suspect there might be a Context leak related to the listener registration. Please analyze the lifecycle handling and suggest a fix if a leak is found."

2.  **Performance Analysis:**
    *   *Less Effective:* "Is the UI performant?"
    *   *More Effective:* "Analyze `ProductListScreen.kt` (Compose UI). Are there potential causes for excessive recomposition? Check the stability of data classes used as state and the usage of `remember`."
    *   *Even Better:* "Review the database query in `LocalDataSource.kt`'s `getProductsByCategory` function. Could this query be a bottleneck, especially with large datasets? Suggest optimizations or indexing strategies if applicable based on the Room entity definition in `ProductEntity.kt` (if provided)."

3.  **Best Practice & Modernization Check:**
    *   *Less Effective:* "Is this code modern?"
    *   *More Effective:* "Evaluate the networking layer implemented in `ApiClient.java`. Does it follow modern practices (e.g., using Retrofit/Ktor, proper error handling, Coroutine integration)? Suggest how to refactor it using Kotlin and Hilt dependency injection based on the patterns seen in other `.kt` files."
    *   *Even Better:* "Assess the state management in `ShoppingCartViewModel.kt`. Is `MutableLiveData` being used appropriately here, or would `StateFlow` or `SharedFlow` be a better fit for representing the cart state and events? Explain why and provide a refactoring example."

4.  **Understanding Interactions:**
    *   *Less Effective:* "How does this feature work?"
    *   *More Effective:* "Trace the user registration flow starting from the button click handler in `RegistrationFragment.java` through `RegistrationViewModel.kt` to the `UserRepository.kt`. Explain the main steps and identify any potential points of failure or areas not following MVVM principles."

5.  **Code Quality & Refactoring:**
    *   *Less Effective:* "Clean up this code."
    *   *More Effective:* "The `processPayment` function in `PaymentHandler.kt` seems overly complex. Please review it for readability, testability, and adherence to the Single Responsibility Principle. Suggest specific refactoring steps."
    *   *Even Better:* "This project uses both XML layouts (`fragment_settings.xml`) and Compose (`ProfileScreen.kt`). Review the way data is passed between the XML Fragment (`SettingsFragment.kt`) and the Compose screen. Is there a cleaner way to manage this interoperability and state sharing, perhaps using a shared ViewModel (`SettingsViewModel.kt`)?"

6.  **Requesting Specific Output:**
    *   *More Effective:* "Generate Kotlin documentation (KDoc) for the public methods in `ImageLoader.kt`."
    *   *Even Better:* "Identify 3 major areas for improvement in `LegacyDataSyncService.java` regarding background execution and lifecycle awareness. For each, explain the issue and provide a concrete code snippet illustrating a modern Android solution (e.g., using WorkManager or appropriate Coroutine scope)."

**Key Takeaway:**

Think of yourself as directing a very knowledgeable but literal assistant. The more precise your instructions, file references, and stated goals, the better the AI can apply its "strict" analysis rules and Android expertise to give you the detailed, high-quality feedback you're looking for. Experiment with phrasing to see what yields the best results.