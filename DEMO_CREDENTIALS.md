# Demo Login Credentials

## Current Setup
The MVP currently uses the **production Supabase database**, so any users you've created in the main project will work here.

## Recommended Demo Accounts

For client demonstrations, create these accounts in your Supabase dashboard:

### Admin Account
- **Email**: `admin@demo.com`
- **Password**: `Admin123!`
- **Role**: Admin

### Cashier Account
- **Email**: `cashier@demo.com`
- **Password**: `Cashier123!`
- **Role**: Cashier

## How to Create Demo Users

### Option 1: Via Supabase Dashboard (Recommended)
1. Go to https://supabase.com/dashboard/project/luhbkhosuawobupmzzrv
2. Navigate to **Authentication** → **Users**
3. Click **"Add user"**
4. Enter email and password
5. After creation, go to **Database** → **Table Editor** → **profiles** table
6. Find the user and set their `role` field to either `admin` or `cashier`

### Option 2: Via SQL (Faster)
Run this SQL in your Supabase SQL Editor:

```sql
-- Create Admin User
INSERT INTO auth.users (
  instance_id,
  id,
  aud,
  role,
  email,
  encrypted_password,
  email_confirmed_at,
  created_at,
  updated_at,
  raw_app_meta_data,
  raw_user_meta_data,
  is_super_admin,
  confirmation_token,
  email_change,
  email_change_token_new,
  recovery_token
) VALUES (
  '00000000-0000-0000-0000-000000000000',
  gen_random_uuid(),
  'authenticated',
  'authenticated',
  'admin@demo.com',
  crypt('Admin123!', gen_salt('bf')),
  now(),
  now(),
  now(),
  '{"provider":"email","providers":["email"]}',
  '{}',
  false,
  '',
  '',
  '',
  ''
);

-- Create Cashier User
INSERT INTO auth.users (
  instance_id,
  id,
  aud,
  role,
  email,
  encrypted_password,
  email_confirmed_at,
  created_at,
  updated_at,
  raw_app_meta_data,
  raw_user_meta_data,
  is_super_admin,
  confirmation_token,
  email_change,
  email_change_token_new,
  recovery_token
) VALUES (
  '00000000-0000-0000-0000-000000000000',
  gen_random_uuid(),
  'authenticated',
  'authenticated',
  'cashier@demo.com',
  crypt('Cashier123!', gen_salt('bf')),
  now(),
  now(),
  now(),
  '{"provider":"email","providers":["email"]}',
  '{}',
  false,
  '',
  '',
  '',
  ''
);
```

**Note**: The SQL approach requires the `pgcrypto` extension to be enabled in your Supabase project.

## Better Approach: Separate Demo Database

For a professional MVP, consider creating a **separate Supabase project** for demos:
1. Create a new Supabase project (free tier)
2. Copy your database schema
3. Add demo users and sample data
4. Update the MVP's Netlify environment variables to point to the demo database

This keeps your production data safe and gives you full control over the demo experience.
