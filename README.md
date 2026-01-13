# A Living Timeline
The Living Timeline is a light projection installation developed for Werkstatt, a bar located in Chur, Switzerland, that highlights the history of the place in a subtle, but meaningful way. Instead of using static archival images, the project brings historical photographs to life by adding gentle AI-generated motion, creating a living, breathing timeline. The projection invites visitors to move upstairs and engage with Werkstatt’s past, reinforcing the importance of its history while remaining respectful to the space and its current use. The installation is designed to be calm, non-intrusive, and adaptable to live events, such as the re-opening event on January 10th, 2026.


## Tools Used
Hardware
- Macbook computer (running TouchDesigner)
- Hanging arm (non-invasive, no drilling required)
- EPSON WXGA projector
- Safety cables

Software
- TouchDesigner (main control and visual logic)
- Google Gemini and Vidu for AI image animation tool
- Premiere Pro for video editing software (behind-the-scenes and results videos)
- Google Drive (hosting the large video files)
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
<img width="1272" height="721" alt="1" src="https://github.com/user-attachments/assets/410bc50f-adf3-4dc8-a743-f4e6e960b2ed" />

2. Timeline Logic to Pre-Composite
<img width="1165" height="524" alt="2" src="https://github.com/user-attachments/assets/9330fcfd-9e51-4ad3-93c7-8ed7d62bc0e3" />

3. Final Projection Output
<img width="1100" height="266" alt="3" src="https://github.com/user-attachments/assets/c1a8fedc-67e4-4a71-9f14-220ca0d50250" />

4. Interface Buttons
<img width="1134" height="569" alt="4" src="https://github.com/user-attachments/assets/6441162c-2977-4673-b756-376c0e7247b1" />


## On-Site Projection
### Projection Test (January 7th)
An on-site testing session was conducted at Werkstatt to adapt the installation to real spatial and technical conditions. The projector was mounted upside down using a non-invasive hanging arm attached to an existing lighting pole. To correct the orientation, a Transform TOP was added to the final projection output, ensuring the images appeared correctly and maintained the intended left-to-right timeline flow. During testing, the Stoner nodes were adjusted on-site to precisely align the projected videos with the physical picture frames on the wall.

Testing under ambient lighting conditions revealed that the default brightness range was insufficient. A Math CHOP was therefore introduced to multiply the brightness value, allowing greater flexibility without permanently increasing intensity. Antialiasing was tested to improve sharpness but was ultimately not applied, as the addition of animated video content already provided sufficient visual clarity. An alternative mapping solution using a single Kantan Mapper was also explored; however, since this was discovered late in the process and the existing setup was stable, the original mapping system was retained for the live event while the alternative was tested separately for learning purposes.

### Final Test & Re-opening Event (January 10th)
During the final test day, we experimented with displaying the frames both with and without the historical images as backgrounds. After testing both options, we chose to keep the images visible behind the animations, as this resulted in a sharper visual appearance and created a stronger, more engaging effect during the event. The frame images were also updated so they matched the corresponding animated videos more accurately, ensuring visual consistency between stills and motion.

While adjusting the videos to fit precisely within the physical frames using the Stoner nodes, we discovered a technical limitation: some videos became cropped when positioned higher, as the video content reached its spatial limits and extended beyond the visible area. Adjusting the projector position slightly helped reduce this issue, although moving it proved challenging due to both the projector’s weight and its hard-to-reach placement. Fortunately, in the area where one video remained slightly cropped, the missing section aligned with a shadow, making the issue visually unnoticeable to viewers.

During the re-opening event, we attempted to further resolve the video cropping issue together with our teacher, Jan, who was present at the event. This included testing adjustments within TouchDesigner and upgrading to a more advanced TouchDesigner license. Despite these efforts, the issue could not be fully resolved during the event, and it has therefore been noted as a point for further investigation beyond the project scope.

As part of the event setup, a sign was placed near the stairs inviting guests to look upstairs and explore the projection. This significantly increased visibility and encouraged visitors to engage with the installation, helping guide attention toward the historical content without interrupting the main event flow.

## Reflection: Making Process
### Planning and Development Process
The project started with the idea of creating a non-distracting installation that still carried strong meaning. Early planning focused on respecting Werkstatt’s identity and physical limitations, such as not being allowed to drill into walls. Development followed an iterative approach: first building a functional timeline system in TouchDesigner, then refining placement, brightness, and interaction during on-site testing.

### Challenges, Rejected Solutions, and Re-planning
Early in the ideation phase, the project explored more visually dominant concepts, including music-reactive projections with strong colors and motion. This direction was later rejected, both because another group was already working with sound-driven visuals and because such an approach risked overwhelming the space during the re-opening event.

After a second visit to Werkstatt and conversations with the owner, the concept was re-planned toward a calmer and more respectful installation focused on historical storytelling. Ideas such as adding purple particle effects around the images were discarded when it became clear that the historical images themselves were central to the space’s identity. This shift led to the final timeline-based concept, designed to support the event rather than compete with it.

Technical challenges emerged during development due to limited experience with TouchDesigner, particularly in building a stable timing system and managing separate outputs for control and projection. Additional difficulties appeared during on-site testing, where projector placement was restricted by the inability to drill into walls. As a result, height and angle were limited, which affected projection coverage.

When aligning the animated videos to the physical frames using Stoner nodes, some content became cropped when positioned higher. Minor improvements were achieved by slightly repositioning the projector, but the issue could not be fully resolved, even during the event. Ideally, a higher-mounted projector dedicated to the images would have reduced both cropping and interference from people passing through the projection path. Due to spatial and resource constraints, these limitations were accepted.

Despite these challenges, the final installation functioned as intended. Positioned upstairs and designed to be non-central, it was received positively and successfully brought Werkstatt’s history to life in a subtle way that aligned with the space and event context.

### Task Distribution
The project was developed by a team of two. Tasks were divided across concept development, TouchDesigner programming, AI image animation, and technical testing. Both members collaborated closely on ideation and decision-making. In addition, the team produced two videos: one documenting the final result and one behind-the-scenes video explaining the setup and process.

### Learning Effect
The project provided hands-on experience with projection mapping constraints, timing systems in TouchDesigner, and the integration of AI-generated content into a real-world installation. It also strengthened skills in adapting concepts to client and spatial requirements, particularly when working under technical and physical limitations.

Overall, the project was a highly rewarding experience. Although working with TouchDesigner was at times challenging and frustrating due to its complexity and our limited prior experience, the process remained engaging and motivating. Seeing the installation function successfully during the re-opening event and observing how visitors interacted with it made the effort worthwhile. The event atmosphere was inspiring, and experiencing the project in a live context reinforced the importance of persistence, collaboration, and iterative problem-solving. This project increased both technical confidence and enthusiasm for working with interactive, spatial, and installation-based media in future projects.
