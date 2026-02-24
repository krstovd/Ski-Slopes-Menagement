# Task

A web application for managing ski slopes needs to be developed.

## Functional Requirements

- On the routes `/` and `/ski-slopes`, display a list of all created ski slopes using the `list.html` template. Additionally, pagination of ski slopes should be enabled.
    - The implementation of this functionality can be verified with the tests `test_list_10pt` and `test_pagination_10pt`.

- Implement adding a new ski slope. When clicking the **Add new ski slope** button from the `list.html` template, the `form.html` template should be displayed on the route `/ski-slopes/add`. After clicking **Submit**, a new ski slope should be created and saved in the database. Then, the `/ski-slopes` page should be displayed.
    - The implementation of this functionality can be verified with the tests `test_create_10pt` and `test_create_mvc_10pt`.

- Implement deleting a ski slope. When clicking the **Delete** button from the `list.html` template, the ski slope should be deleted from the database. Then, the `/ski-slopes` page should be displayed.
    - The implementation of this functionality can be verified with the tests `test_delete_3pt` and `test_delete_mvc_2pt`.

- Implement editing ski slope details. When clicking the **Edit** button from the `list.html` template, the `form.html` template should be displayed on the route `/ski-slopes/edit/[id]`, where the `<input>` elements will contain the values of the ski slope being edited. After clicking **Submit**, the changes should be saved in the database. Then, the `/ski-slopes` page should be displayed.
    - The implementation of this functionality can be verified with the tests `test_edit_10pt` and `test_edit_mvc_10pt`.

- Implement closing a ski slope if it is open. When clicking the **Close** button from the `list.html` template, the corresponding field in the model should be updated. Then, the `/ski-slopes` page should be displayed.
    - The implementation of this functionality can be verified with the tests `test_close_slope_3pt` and `test_close_slope_mvc_2pt`.

- Configure login at `/login` and logout at `/logout`. The routes `/` and `/ski-slopes` should be public, while all other pages should be accessible only to a user with the admin role. Additionally, in `list.html`, the buttons **Edit**, **Delete**, **Add new ski slope**, and **Close** should be visible only to users with the admin role. The **Close** button should be visible only if the ski slope is open.
    - The implementation of this functionality can be verified with the tests `test_security_urls_10pt` and `test_security_buttons_10pt`.

- Enable searching of ski slopes by name (whether the submitted text is contained in the `name` variable), ski slope length (slopes longer than the entered length), ski slope difficulty, and ski resort through the form with `id="filter-form"` in the `list.html` template. The search results should be displayed on the same page, showing only ski slopes whose names contain the submitted text, have a greater length than the entered value, match the selected difficulty, and belong to the selected ski resort. Filtering is performed only according to the entered fields (if they are empty, filtering by that criterion is ignored).
    - The implementation of this functionality can be verified with the tests `test_filter_5pt` and `test_filter_service_5pt`.


## Technical Instructions

- In the package `mk.ukim.finki.wp.kol2025g2.model`, the classes representing the model are already created. You need to map them with the appropriate JPA annotations so that the model can be successfully saved in the database.
  The following conditions apply:
    - One ski slope belongs to exactly one ski resort, while one ski resort can have multiple ski slopes.
    - The identifiers for `SkiSlope` and `SkiResort` should be automatically generated.

- In the package `mk.ukim.finki.wp.exam.kol2025g2.service`, the service logic interfaces are already defined. Each method contains a description of what needs to be implemented. These interfaces should be implemented in the appropriate classes in the package `mk.ukim.finki.wp.exam.kol2025g2.service.impl`. Additional conditions (if any) are explained in the method comments.

- The classes in the package `mk.ukim.finki.wp.exam.kol2025g2.repository` should be extended with the necessary methods required to enable the functionality of the service layer implementation. They should extend `JpaRepository` from Spring Data.

- Annotate the `DataInitializer` class and its corresponding methods so that the `initData` method is executed when the application starts.

- In the class `mk.ukim.finki.wp.exam.kol2025g2.SkiSlopeController`, all required methods are defined. Each method includes a description of what needs to be implemented. These handler methods should be mapped using only HTTP GET and POST requests.

- Complete the templates with the appropriate **Thymeleaf** attributes to achieve the required functionalities. If certain elements or attributes are missing, you may add them, but you must NOT modify the existing `id` and `class` properties of the elements.
  Comments describe which elements should be repeated and which controller methods should be invoked.

- Configure login and logout using Spring Security in the `SecurityConfig` class.
  The class itself contains a description of what needs to be implemented.
