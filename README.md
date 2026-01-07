# A Living Timeline
The Living Timeline is a light projection installation developed for Werkstatt, a bar located in Chur, Switzerland, that highlights the history of the place in a subtle, but meaningful way. Instead of using static archival images, the project brings historical photographs to life by adding gentle AI-generated motion, creating a living, breathing timeline. The projection invites visitors to move upstairs and engage with Werkstatt’s past, reinforcing the importance of its history while remaining respectful to the space and its current use. The installation is designed to be calm, non-intrusive, and adaptable to live events, such as the re-opening event on January 10th, 2026.


## Tools Used
Hardware
- Macbook computer (running TouchDesigner)
- Hanging arm (non-invasive, no drilling required)
- EPSON WXGA Projector 

Software
- TouchDesigner (main control and visual logic)
- Google Gemini for AI image animation tool
- Premiere Pro for video editing software (documentation and behind-the-scenes videos)
- Google Drive (hosting large video files)
- GitHub (uploading final project)


## Process
This section describes the overall process and technical logic behind the project, explaining how the installation was built step by step and how the different elements work together to create the living timeline.

1. Prepare the visual content
- Collect four historical images related to the location. These images are physically placed horizontally next to each other in the space.
- Use Google Gemini to add subtle movement to each image. Export each result as a short video.

2. Set up TouchDesigner
- Open TouchDesigner and create a new project.
- Import the four AI-generated videos as TOPs (one per historical image).

3. Create the timing system
- Build a timer and count system using CHOPs that controls how long each image is highlighted.
- Set the count to loop from 0 to 3, so the system cycles through the four images continuously.

4. Highlight one image at a time
- Add a Level TOP to each video.
- Use expressions in the opacity parameter so only one image is visible at a time:
  - Image 1 visible when count = 0
  - Image 2 visible when count = 1
  - Image 3 visible when count = 2
  - Image 4 visible when count = 3
- This creates a left-to-right highlight effect, where one image is projected and subtly animated while the others are not highlighted.

5. Switch and positioning
- Connect the videos to a Level TOP to manage selection.
- Add a Stoner container to each image to precisely match the physical frames on the wall, which was done during on-site testing.

6. Override: show all images
- Add a Switch TOP that overrides the timeline logic and displays all four images at the same time. - This allows switching between a guided timeline mode and a full overview mode. We connected this to a button.
  
7.  Final composition and output
- Connect each Stoner to a Null TOP and combine them in a COMP with a fixed output resolution.
- Add a final Level TOP to control the brightness with a slider.
- Connect the final output to a Window COMP and configure the following settings so the controls remain visible on the computer while displaying only the final output on the projector:
  - Select projector as target monitor (verified via Monitors DAT).
  - Set Opening Size to Fill.
  - Disable Borders.
  - Enable Always on Top.
- Add interface buttons to:
  - Open projection as a separate window.
  - Close the projection window.


## Visual Documentation
This section presents screenshots and photos that document the development and outcome of the living timeline installation. 

### TouchDesigner Screenshots
1. Complete Project Network Overview

2. Timeline Logic to Pre-Composite

3. Final Projection Output

4. Interface Buttons


## On-Site Projection
### Projection Test (January 7th)
An on-site testing session was conducted at Werkstatt to adapt the installation to real spatial and technical conditions. The projector was mounted upside down using a non-invasive hanging arm attached to an existing lighting pole. To correct the orientation, a Transform TOP was added to the final projection output, ensuring the images appeared correctly and maintained the intended left-to-right timeline flow. During testing, the Stoner nodes were adjusted on-site to precisely align the projected videos with the physical picture frames on the wall.

Testing under ambient lighting conditions revealed that the default brightness range was insufficient. A Math CHOP was therefore introduced to multiply the brightness value, allowing greater flexibility without permanently increasing intensity. Antialiasing was tested to improve sharpness but was ultimately not applied, as the addition of animated video content already provided sufficient visual clarity. An alternative mapping solution using a single Kantan Mapper was also explored; however, since this was discovered late in the process and the existing setup was stable, the original mapping system was retained for the live event while the alternative was tested separately for learning purposes.

### Re-opening Event (January 10th)


## Reflection: Making Process
### Planning and Development Process
The project started with the idea of creating a non-distracting installation that still carried strong meaning. Early planning focused on respecting Werkstatt’s identity and physical limitations, such as not being allowed to drill into walls. Development followed an iterative approach: first building a functional timeline system in TouchDesigner, then refining placement, brightness, and interaction during on-site testing.

### Challenges, Rejected Solutions, and Re-planning
Initially, we considered creating a large, colorful projection driven by music, with strong visual reactions and higher intensity. However, another group was already working on a music-controlled installation for the event. To avoid visual overload and distraction during the re-opening, this approach was consciously rejected.

After a second visit to Werkstatt and conversations with the owner, the focus shifted toward a more subtle and meaningful solution. Early ideas included purple particle movements around the images, inspired by Werkstatt’s lighting identity. This idea was later discarded when the owner explained that the images upstairs represented how the place originally looked. Combined with the planned historical speech during the event, this insight led to the final concept: highlighting the history itself rather than decorating it.

Technical challenges mainly came from spatial limitations. The projector placement was restricted by the fact that no drilling was allowed, which required careful planning of height and distance. TouchDesigner was also new to us, leading to difficulties in building the correct network logic and managing dual outputs (projector vs. computer screen). Some issues appeared when reopening the file, such as window placement extending beyond the screen, which required manual adjustments.

### Task Distribution
The project was developed by a team of two. Tasks were divided across concept development, TouchDesigner programming, AI image animation, and technical testing. Both members collaborated closely on ideation and decision-making. In addition, the team produced two videos: one documenting the final result and one behind-the-scenes video explaining the setup and process.

### Learning Effect
The project provided hands-on experience with projection mapping constraints, timing systems in TouchDesigner, and the integration of AI-generated content into a real-world installation. It also strengthened skills in adapting concepts to client and space requirements.
