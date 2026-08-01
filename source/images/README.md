# Images Directory

This directory contains image assets for your blog.

## Avatar Setup

To add your avatar:

1. **Prepare your avatar image:**
   - Recommended size: 200x200 pixels or larger
   - Format: GIF, PNG, or JPG
   - Keep file size under 100KB for better performance

2. **Add your avatar:**
   - Place your avatar file as `avatar.gif` in this directory
   - Or update the path in `_config.next.yml`:
     ```yaml
     avatar:
       url: /images/your-avatar.png
       rounded: true
       rotated: false
     ```

3. **Current configuration:**
   - The theme is configured to look for `/images/avatar.gif`
   - If you don't have an avatar, the theme will use a default icon

## Other Images

You can organize your images in subdirectories:

- `/images/posts/` - Images for blog posts
- `/images/about/` - Images for the about page
- `/images/banner/` - Banner or header images

## Image Optimization Tips

- Compress images before uploading
- Use appropriate formats (PNG for graphics, JPG for photos)
- Consider using WebP format for better compression
- Keep image sizes reasonable for web performance

## Post Images

When writing blog posts, you can reference images like this:

```markdown
![Image description](/images/posts/your-image.jpg)
```

Or use post asset folders (enable with `post_asset_folder: true` in `_config.yml`).
