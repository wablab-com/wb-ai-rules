# Code Structure

- Keep methods and classes focused; split large logic into well-named helpers when it improves readability.
- Use meaningful names and minimize coupling.
- Prefer the repository's existing architecture, libraries, dependency injection patterns, error handling, and test style.
- Keep controllers, handlers, commands, and UI callbacks thin; place reusable business logic in services or domain modules appropriate to the project.
- Avoid broad refactors unless they are necessary for the requested change or explicitly approved.
